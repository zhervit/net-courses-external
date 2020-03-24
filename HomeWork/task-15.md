## Технология ADO.NET. Практическая часть

#### Задание 1
Для приложения «Пользователи и награды» использовать спроектированную в прошлом задании базу данных для хранения информации о пользователях и наградах. 
Для приложения «Пользователи и награды» из предыдущего задания необходимо добавить ещё одну реализацию слоя доступа к данным, таким образом, чтобы данные о пользователях и наградах хранились в базе данных, выполненной в предыдущем задании. 
Требования:
*	Использовать присоединённую модель ADO.NET.
*	Строка подключения в БД должна считываться из файла конфигурации
*	В файле конфигурации должна быть настройка, позволяющая выбирать используемы слоё доступа к данным (БД или коллекции). 

## Процедуры

```sql

USE [UsersAndRewards]
GO

CREATE PROCEDURE [dbo].[GetUserRewards](@userId int)
AS

SELECT Rewards.RewardId, Title, [Description]
	FROM Rewards INNER JOIN UserRewards ON Rewards.RewardId = UserRewards.RewardId
		WHERE UserId = @userId


GO

CREATE PROCEDURE [dbo].[GetUsers]
As
	SELECT UserId, [FirstName], [LastName], [Birthdate]
		FROM [User]


GO

CREATE PROCEDURE [dbo].[InsertUser](
	@firstName nvarchar(100),
	@lastName nvarchar(100),
	@birthdate datetime)
As
	INSERT INTO [User](FirstName, LastName, Birthdate)
		OUTPUT INSERTED.UserId
			VALUES(@firstName, @lastName, @birthdate)

GO

CREATE TYPE dbo.Rewards AS TABLE
(
  RewardId INT
);
GO

CREATE PROCEDURE [dbo].[InsertUserRewards](
	@userId int,
	@rewardIds AS dbo.Rewards READONLY)
As
	INSERT INTO UserRewards(UserId, RewardId)
		SELECT @userId, RewardId FROM @rewardIds

GO

```
