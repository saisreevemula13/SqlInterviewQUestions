# SqlInterviewQUestions

1.Write string reversal program
2.Functions vs SP
3.Why SP doesn't return multiple values
Unlike functions SP doesn't multiple values. In order to make SP return multiple values we use below ways
  i)use multiple OUTPUT parameters
  CREATE PROCEDURE printEmployeeDetails
  ( @EmployeeID INT, 
    @EmployeeName VARCHAR(20),
    @EmployeeSalary Decimal(18,2))
  AS BEGIN
  SELECT @EmployeeName=Name, @EmployeeSalary=Salary FROM Employees
  WHERE EmployeeId=@EmployeeID
  END
  ---
  calling sp
  DECLARE @Name NVARCHAR(20), @Salary Decimal(18,2)
  EXEC printEmployeeDetails
  @EmployeeName = @Name OUTPUT, 
  @EmployeeSalary = @Salary OUTPUT;
  ---
  
