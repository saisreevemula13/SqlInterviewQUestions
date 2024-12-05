# SqlInterviewQUestions

1.Write string reversal program
2.Functions vs SP
3.Why SP doesn't return multiple values
Unlike functions SP doesn't multiple values. In order to make SP return multiple values we use below ways
  i)use multiple OUTPUT parameters-here we have two outputs, 
  ----
  CREATE PROCEDURE printEmployeeDetails
  ( @EmployeeID INT, 
    @EmployeeName VARCHAR(20),
    @EmployeeSalary Decimal(18,2))
  AS BEGIN
  SELECT @EmployeeName=Name, @EmployeeSalary=Salary FROM Employees
  WHERE EmployeeID=@EmployeeID
  END
  
  calling sp
  DECLARE @Name NVARCHAR(20), @Salary Decimal(18,2)
  EXEC printEmployeeDetails
  @EmployeeID=1
  @EmployeeName = @Name OUTPUT, 
  @EmployeeSalary = @Salary OUTPUT;
  
  ii)Use a select statement for retrival of multiple rows,coulumns
----
  CREATE PROCEDURE GetEmpDetails
  ( @EmployeeID INT)
  AS 
  BEGIN
  SELECT EmpID,EMpName,EmpSalary FROM Employee WHERE EmployeeID=@EmployeeID
  END;
  ---
  EXEC GetEmpDetails @EmployeeID=13
  iii)For complex result set returning we use temprory table
  CREATE PROCEDURE GetStudDetails
  AS
BEGIN
  DECLARE @StudTABLE TABLE (StudID INT,StudName NVARCHAR(100),StudCity NVARCHAR(100))
INSERT INTO @StudTABLE(StudID,STudName,StudCity)
SELECT StudID,STudName,StudCity FROM Students;
SELECT * FROM #StudTABLE;
END
EXEC GetStudDetails;
iv)A stored procedure can return multiple result sets (tables) by executing multiple SELECT statements within the same procedure.
CREATE PROCEDURE GetMultipleResultSets
AS
BEGIN
    -- First result set
    SELECT EmployeeID, Name FROM Employees;
    
    -- Second result set
    SELECT DepartmentID, DepartmentName FROM Departments;
END
EXEC GetMultipleResultSets;



  

  
  
