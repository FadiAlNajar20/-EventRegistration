# Event Registration System

## Overview
The **Event Registration System** is an ASP.NET Core MVC application that allows users to register for events and receive confirmation emails. This system provides event organizers with the ability to create, update, and delete events, while users can browse, register, and receive notifications for events via email.

## Features
- ASP.NET Core MVC-based event management system.
- Implements CRUD operations for events and registrations.
- Integrated with Mailjet for sending confirmation emails.
- Uses Entity Framework Core with SQL Server for database management.
- Form validation for event creation and registration.
  
## Prerequisites
Before you begin, ensure you have the following installed:
- [.NET 6.0 SDK](https://dotnet.microsoft.com/download)
- [SQL Server](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
- [Visual Studio 2022](https://visualstudio.microsoft.com/) or [Visual Studio Code](https://code.visualstudio.com/)
- Mailjet account for email notifications.

## Setup Instructions

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/event-registration-system.git
cd event-registration-system
```

### 2. Configure Database Connection
Set up the connection to your SQL Server database in `appsettings.json`:

```json
"ConnectionStrings": {
  "DefaultConnection": "Server=your_server;Database=EventRegistrationDB;Trusted_Connection=True;MultipleActiveResultSets=true"
}
```

Make sure to replace `your_server` with your actual SQL Server name or instance.

### 3. Install Required Packages
Run the following command to install the necessary NuGet packages for the project:

```bash
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
dotnet add package Microsoft.EntityFrameworkCore.Tools
dotnet add package Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation
dotnet add package Microsoft.EntityFrameworkCore.Design
dotnet add package Mailjet.Api --version 3.0.0
```

Alternatively, you can install them using the NuGet Package Manager in Visual Studio.

### 4. Set Up Mailjet for Email Notifications
In your `appsettings.json`, add your Mailjet API credentials:

```json
"Mailjet": {
  "ApiKey": "your_mailjet_api_key",
  "SecretKey": "your_mailjet_secret_key"
}
```

You can obtain your API key and secret from [Mailjet's website](https://www.mailjet.com/).

### 5. Update Database
Run the following commands to create the database and apply migrations:

```bash
dotnet ef migrations add InitialCreate
dotnet ef database update
```

This will create the necessary tables for events and registrations in your SQL Server database.

### 6. Build and Run the Application
Once everything is set up, you can build and run the application:

```bash
dotnet build
dotnet run
```

Open your browser and navigate to `http://localhost:5000` to see the app running.

## Event Management

You can manage events by navigating to the events section. The system allows for creating, editing, and deleting events, with validation on forms to ensure correct input.

## Registration Process

Participants can register for events by selecting an event from the list and filling out the registration form. Upon successful registration, they will receive a confirmation email via Mailjet.

### 7. Testing the Email Functionality
- Ensure that your Mailjet API key and secret are correctly configured.
- After a participant registers for an event, the email service will trigger and send a confirmation email.
- You can check Mailjet logs or your email inbox to confirm that the email was sent successfully.

## Troubleshooting

- **Mailjet issues:** Make sure the API key and secret are correct, and Mailjet is not blocking any email requests.
- **Database connection errors:** Ensure that SQL Server is running, and the connection string is correctly set in `appsettings.json`.
- **Missing migrations:** If migrations are not applying, ensure Entity Framework Core is correctly installed.