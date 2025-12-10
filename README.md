## Description

Library App is a .NET 8 console application that manages a library system. It allows users to search for patrons, view their loan history, renew memberships, extend book loans, and return borrowed items. The application uses a JSON-based data persistence layer and follows a clean architecture pattern with separated concerns across application core, infrastructure, and presentation layers.

## Project Structure

```
AccelerateDevGitHubCopilot/
├── README.md
├── AccelerateDevGitHubCopilot.sln
├── src/
│   ├── Library.ApplicationCore/
│   │   ├── Library.ApplicationCore.csproj
│   │   ├── Entities/
│   │   │   ├── Author.cs
│   │   │   ├── Book.cs
│   │   │   ├── BookItem.cs
│   │   │   ├── Loan.cs
│   │   │   └── Patron.cs
│   │   ├── Enums/
│   │   │   ├── EnumHelper.cs
│   │   │   ├── LoanExtensionStatus.cs
│   │   │   ├── LoanReturnStatus.cs
│   │   │   └── MembershipRenewalStatus.cs
│   │   ├── Interfaces/
│   │   │   ├── ILoanRepository.cs
│   │   │   ├── ILoanService.cs
│   │   │   ├── IPatronRepository.cs
│   │   │   └── IPatronService.cs
│   │   └── Services/
│   │       ├── LoanService.cs
│   │       └── PatronService.cs
│   ├── Library.Console/
│   │   ├── Library.Console.csproj
│   │   ├── Program.cs
│   │   ├── ConsoleApp.cs
│   │   ├── ConsoleState.cs
│   │   ├── CommonActions.cs
│   │   ├── appSettings.json
│   │   └── Json/
│   │       ├── Authors.json
│   │       ├── Books.json
│   │       ├── BookItems.json
│   │       ├── Loans.json
│   │       └── Patrons.json
│   └── Library.Infrastructure/
│       ├── Library.Infrastructure.csproj
# Library App

## Description

`Library App` is a .NET 8 console application that models a simple library system. It lets you search for patrons, view loan history, renew memberships, extend loans, and return books. The application uses JSON files for persistence and follows a layered structure (application core, infrastructure, console UI) to separate responsibilities.

## Project Structure

- `AccelerateDevGitHubCopilot/`
    # Library App

    ## Description

    `Library App` is a .NET 8 console application that models a simple library system. It lets you search for patrons, view loan history, renew memberships, extend loans, and return books. The application uses JSON files for persistence and follows a layered structure (application core, infrastructure, console UI) to separate responsibilities.

    ## Project Structure

    - `AccelerateDevGitHubCopilot/`
        - `AccelerateDevGitHubCopilot.sln`
        - `src/`
            - `Library.ApplicationCore/`
                - `Library.ApplicationCore.csproj`
                - `Entities/`
                    - `Author.cs`
                    - `Book.cs`
                    - `BookItem.cs`
                    - `Loan.cs`
                    - `Patron.cs`
                - `Enums/`
                    - `EnumHelper.cs`
                    - `LoanExtensionStatus.cs`
                    - `LoanReturnStatus.cs`
                    - `MembershipRenewalStatus.cs`
                - `Interfaces/`
                    - `ILoanRepository.cs`
                    - `ILoanService.cs`
                    - `IPatronRepository.cs`
                    - `IPatronService.cs`
                - `Services/`
                    - `LoanService.cs`
                    - `PatronService.cs`
            - `Library.Console/`
                - `Library.Console.csproj`
                - `Program.cs`
                - `ConsoleApp.cs`
                - `ConsoleState.cs`
                - `CommonActions.cs`
                - `appSettings.json`
                - `Json/`
                    - `Authors.json`
                    - `Books.json`
                    - `BookItems.json`
                    - `Loans.json`
                    - `Patrons.json`
            - `Library.Infrastructure/`
                - `Library.Infrastructure.csproj`
                - `Data/`
                    - `JsonData.cs`
                    - `JsonLoanRepository.cs`
                    - `JsonPatronRepository.cs`
        - `tests/`
            - `UnitTests/`
                - `UnitTests.csproj`
                - `PatronFactory.cs`
                - `LoanFactory.cs`
                - `ApplicationCore/`
                    - `LoanService/` (tests)
                    - `PatronService/` (tests)

    > Notes: `.gitignore`, `.github`, `bin/` and `obj/` folders are intentionally omitted from this listing.

    ## Key Classes and Interfaces

    - Entities
        - `Patron` — Represents a library patron with membership data and associated loans.
        - `Loan` — Represents a loan (loan date, due date, return date, related `BookItem`).
        - `Book` — Represents a book title and metadata.
        - `BookItem` — Represents a physical copy of a book.
        - `Author` — Represents an author.

    - Services
        - `ILoanService` / `LoanService` — Contains business logic to extend and return loans.
        - `IPatronService` / `PatronService` — Contains logic to renew patron memberships.

    - Repositories
        - `ILoanRepository` / `JsonLoanRepository` — Data access for loans (JSON-backed).
        - `IPatronRepository` / `JsonPatronRepository` — Data access for patrons (JSON-backed).
        - `JsonData` — Central loader and in-memory holder for JSON files; provides helper methods to populate relationships.

    - Console UI
        - `ConsoleApp` — Main interactive CLI that drives a state machine to search patrons and manage loans.
        - `ConsoleState` — Enum representing UI states (search, details, loan view, etc.).
        - `CommonActions` — Action flags used by the UI.

    ## Usage

    ### Build

    ```powershell
    dotnet build AccelerateDevGitHubCopilot.sln
    ```

    ### Run the console application

    ```powershell
    dotnet run --project src/Library.Console/Library.Console.csproj
    ```

    When started, the app prompts for a patron search. Use the interactive options to view details, renew membership, extend loans, or return books.

    Common actions (keys used by the console UI):

    - `m` — Renew membership
    - `e` — Extend a loan
    - `r` — Return a loan
    - `s` — Search for a patron
    - `q` — Quit the app

    ### Run unit tests

    ```powershell
    dotnet test tests/UnitTests/UnitTests.csproj
    ```

    ### Configuration

    Paths to JSON data are configured in `src/Library.Console/appSettings.json`. Modify the `JsonPaths` section to point to alternative data files or directories.

    ## License

    This project is provided as-is for educational and development purposes. No formal license is included in the repository unless you add one. If you plan to reuse or redistribute the code, consider adding a license (for example, `MIT`) and a `LICENSE` file.