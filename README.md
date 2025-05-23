# GitHub Copilot Hands-On Lab
This is a simplified version of the GitHub Copilot Hands-On Lab for quickly ramp-up GitHub Copilot. The original version is available at [GitHub Copilot Hands-On Lab](https://learn.microsoft.com/en-us/training/paths/accelerate-app-development-using-github-copilot/
)

## 0. Prerequisites
- Config GitHub Copilot in you VS Code.
    - Install the GitHub Copilot extension @id:github.copilot
    - Install the GitHub Copilot Chat extension @id:GitHub.copilot-chat.
    - Sign in with your GitHub Enterprise account.
- Install VS Code C# Dev Kit extension @id:ms-dotnettools.csdevkit
- Download the SampleApps for the hands-on lab https://raw.githubusercontent.com/xiaoliangshi/GitHubCopilotHandsOnLab/refs/heads/main/Lab_SampleApps.zip

---

## 1. Code Explanation & Document Generation

### 1.1 Code Explanation

### 1.1.1 Project explanation


1. Open the folder `APL2007M2Sample1` with VS Code.
2. Open Chat `Ctrl + Alt + i`
3. Type the prompt to explain the project.

    ```
    @workspace Explain this project
    ```
### 1.1.2 File explanation
1. Open the file `MainWindow.xaml.cs`.
2. Ask copilot to explain the file.

    ```
    @workspace /explain #file:MainWindow.xaml.cs
    ```
### 1.1.3 Selected code explanation
1. In file `MainWindow.xaml.cs`, locate the method `SumPageSizesAsync()`, select the following code lines.

    ```C#
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in _urlList
        select ProcessUrlAsync(url, _client);

    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```
2. Right click to open the context menu ``Copilot > Explain``.

### 1.1.4 Error explanation
1. In file `MainWindow.xaml.cs`, locate the method `SumPageSizesAsync()`, select the following code line.
    ```C#
    int[] lengths = Task.WhenAll(downloadTasks);
    ```
2. Open inline chat ``Ctrl + i``, enter the prompt to ask for the error.

    ```
    /explain why is the selection causing an error
    ```

3. Right click to open the context menu ``Copilot > Fix``. Fix the error by changing the code to: 
    ```C#
    int[] lengths = await Task.WhenAll(downloadTasks);
    ```
### 1.2 Document Generation
### 1.2.1 Generate README file
1. Open the folder `APL2007M2Sample1` with VS Code.
2. Open chat ``Ctrl + Alt + i``, enter the prompt to generate a README file.

    ```
    @workspace generate a readme document that can be used as a repo description
    ```
### 1.2.2 Generate inline code documentation
1. Open the file `MainWindow.xaml.cs`.
2. Select all the code lines.
3. Open chat ``Ctrl + Alt + i``, enter the prompt to generate a README file. Generate inline code documentation with copilot chat.

    ```
    @workspace generate inline code documentation for the selected code
    ```
4. Select the code lines for the function `OnStartButtonClick`, open inline edit with `Ctrl + i` Generate inline code documentation with inline chat
    
    ```
    /doc
    ```

---

## 2. Dev Codes

### 2.1 Inline Code Generation from a comment
1. Open the folder `APL2007M4PrimeService` with VS Code.
2. In the file `PrimeService.cs`, locate the class `PrimeService`.
3. Add a comment above the class to generate the method `IsPrime`.
    ```C#
    // Generate a method named IsPrime that takes an integer as input and returns a boolean indicating whether the number is prime or not.
    ```
### 2.2 Inline Code generation from a method signature
1. In the file `PrimeService.cs`, locate the class `PrimeService`.
2. Add a method signature for the function `IsPrime` with the return type `bool` and input parameter `int number`.
    ```C#
    public bool IsPrime(int number)
    ```
### 2.3 Code Generation from an inline chat/GitHub Copilot chat
1. Open the file `PrimeService.cs`
2. Open the GitHub Copilot chat `Ctrl + Alt + i`
    ```
    Generate a method named IsPrime that takes an integer as input and returns a boolean indicating whether the number is prime or not.
    ```

---

## 3. Unit Tests

### 3.1 Create unit tests using Chat view
1. Open the folder `APL2007M4PrimeService` with VS Code.
2. Select the code lines for the function `IsPrime`.
3. Open the GitHub Copilot chat `Ctrl + Atl + i`, add context `PrimeService.UnitTests.csproj.` and `PrimeServiceTests.cs`
4. Generate the unit test code with below prompt.
    ```
    /tests add unit tests for my code
    ```
5. Build & Run the tests
### 3.2 Create unit tests using inline chat
1. Curser to the function `IsPrime`, Open the GitHub Copilot chat `Ctrl + i`
2. Try the prompt below to generate unit tests.
    ```
    Create unit tests for the IsPrime method using the xUnit framework.
    ```
### 3.3 Create unit for specific cases
1. Open the GitHub Copilot chat `Ctrl + Atl + i`
2. Try the prompt below to generate unit tests for specific cases.
    ```
    @workspace are there any edge cases that should also be tested
    ```
---
