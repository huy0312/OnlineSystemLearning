# Online Learning Platform

## Introduction
Online Learning Platform is a web application developed using ASP.NET CORE MVC. The goal of the project is to provide an online learning platform for students and instructors, optimizing course management, tracking learning progress, and enhancing the learning experience.

## Key Features
### Mentee
- Register and log in.
- View and enroll in courses.
- Track learning progress and assignments.
- Rate and review courses.
- Purchase course, Deposit money to wallet
- Chat message to mentor

### Mentor
- Create and manage courses.
- Upload learning materials and lectures.
- Monitor student progress.

### Admin
- Manage users (mentees and mentors).
- Manage course categories.
- Approve and moderate course content.

### AI
- Review Course content to approve or reject.
- Support member 24/7

## Technologies Used
- **Programming Language**: C#
- **Framework**: ASP.NET CORE MVC
- **Database**: SQL Server
- **Front-end**: HTML, CSS, JavaScript, Bootstrap
- **Version Control**: Git

## Project Structure
```
OnlineLearningPlatform/
├── wwwroot/
├── Configurations/
├── Controllers/
├── Data/
├── Enum/
├── Migrations/
├── Models/
├── Repositories/
├── Services/
├── Views/
├── appsettings.json
└── Program.cs
```

### Key Directories
- **wwwroot**: Contains JavaScript, CSS, Images files, and other static resources.
- **Configurations**: Contains configurations to config in Program.cs.
- **Controllers**: Contains controllers to handle application logic.
- **Data**: Contains DBContext and SeedConfigurationData.
- **Migrations**: Entity Framework Core Migrations.
- **Models**: Contains classes representing data.
- **Repositories**: Contains logic query database, call DBContext.
- **Services**: Contains business logic, call Repository.
- **Views**: Contains Razor files for rendering content.
- **appsettings.json**: Configs application
- **Program.cs**: Start point

## Installation Guide
1. **System Requirements**:
   - Visual Studio 2022 (or later).
   - SQL Server 2019 (or higher).
   - .NET 8.0 (or higher).

2. **Clone the repository**:
   ```bash
   git clone https://gitlab.com/prn2221/online-learning.git
   ```
3. **Setup appsetting.json**:
   - Open Solution: OnlineLearning.sln
   - Open terminal solution, run:
   ```bash
   copy appsettings_TEMPLATE.json appsettings.json
   ```
   - Mở file appsettings.json and update StringConnect - OLS.
   - Build Solution

4. **Initialize the database**:
   - If chưa cài dotnet ef, run command: 
   ```bash
   dotnet tool install --global dotnet-ef
   ```
   hoặc update dotnet ef:
   ```bash
   dotnet tool update --global dotnet-ef
   ```
   - Finally, Run command: 
   ```bash
   dotnet ef database update
   ```
5. **Run the application**:
   - Run the application.
   - Open browser and go to:
   ```bash
   https://localhost:8686
   ```

## Authors
- **Development Team**: Online Learning Team PRN222
- **Contact**: systemonlinelearning@gmail.com

## Contribution
We welcome contributions from the community. If you'd like to contribute, please create a pull request or contact us via the email above.

## License
This project is licensed under the MIT License. Please refer to the `LICENSE` file for details.

## Git flow
Nếu chưa tạo branch, (code tính năng mới):
- B1: Tạo issue trên gitlab.
- B2: Tạo branch cho issue đấy. -> tiếp bên dưới luôn

Nếu đang code dở, mà qua lười code để nay code nốt:
- B3: Open git bash or cmd trong project
- B4: run command ``` git checkout dev ``` để chuyển về nhánh dev
- B5: run command ``` git pull ``` để pull code mới nhất về (quan trọng để tránh bị conflict)
- B6: run command ``` git checkout <your_branch> ``` để chuyển sang branch của mình
- B7.1: run command ``` git merge dev ``` để merge code mới nhất trên dev
- B7.2: nếu ae bị conflict ở đây thì xem xem code nào ko phải của mình thì accept code mới nhé. Còn code mình đang dev thì accept my code (để tránh bị mất code người khác)
- B8: code thoii!
- B9: run command ``` git add . ``` để push code lên git local
- B10: run command: ``` git commit -m" <commit_cua_minh> " ``` để commit
- B11: run command: ``` git push ``` để push code lên git global
- B12: Mở project trên gitlab, chuyển sang branch của mình
- B13: Tạo Merge Request
- B14: nếu không bị conflict thì merge thôi:
       nhớ bỏ chọn 'Delete source branch when merge request is accepted.' để không bị xóa branch, phòng trường hợp có bug thì fix lại trên branch đó
       và chọn 'Squash commits when merge request is accepted.' để squash nhiều commits lại thành 1 commit khi merge vào dev để nếu có bug thì rollback lại version cũ dễ
- B15: xong ròi cho tròn số thôi

## How to code
- Controller → Nhận request, gọi Service (Xử lý logic nghiệp vụ).
- Service → Chứa business logic, gọi Repository (Làm việc với database).
- Repository → Chứa logic truy vấn database, gọi DbContext (Truy vấn dữ liệu).
	```
	/Controllers
   ├── UserController.cs
	/Services
   ├── IUserService.cs
   ├── UserService.cs
	/Repositories
   ├── IUserRepository.cs
   ├── UserRepository.cs
	/Data
   ├── ApplicationDbContext.cs
	/Models
   ├── User.cs
	```
- B1: Tạo interface I_Repository
- B2: Tạo class _Repository implements I_Repository
- B3: Tạo interface I_Service
- B4: Tạo class _Service implements I_Service
- B5: DI trong Program.cs:
	```
	builder.Services.AddScoped<I_Repository, __Repository>();
	builder.Services.AddScoped<I_Service, _Service>();
	```
- B6: Tạo _Controller ròi code hoii!!
- Hello