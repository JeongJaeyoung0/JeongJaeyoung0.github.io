---
layout: post
title: "[DB] DB 연결 방법"
subtitle: "DbSetting"
categories: other
tags: db
comments: true
---

# DB 연결 방법

1. Visual Studio > 확장 > 확장 관리> EF Core Power Tool 설치

2. MySQL for Visual Studio 설치

3. Nuget 패키지 관리 > Pomelo.EntityFrameworkCore.MySql 설치

4. 프로젝트 우클릭 > EF Core Power Tool > Reverse Engineer > MySql 변경 및  정보 입력

5. Startup.cs > services.AddControllersWithViews(); > 아래 줄에 코드 추가
  ```
  //DB 연결 세팅
  ConnectionString = Configuration.GetConnectionString("DefaultConnection");
  services.AddDbContext<//Context이름 입력//>(options => options.UseMySql(ConnectionString, //Context에 접속 정보 관련 버전 복붙 Microsoft.EntityFrameworkCore.ServerVersion.Parse("10.6.5-mariadb")//));
  services.AddControllersWithViews();
  services.AddSingleton<IConfiguration>(Configuration);
  services.AddSingleton<IHttpContextAccessor, HttpContextAccessor>();
  ```

6. 변수 선언
  ```
  string ConnectionString = null;
  ```

7. appsettings.json > 코드 추가
  ```
  "ConnectionStrings": {
    "DefaultConnection": "//Context에 접속 정보 복붙 server=127.0.0.1;user id=root;password=0000;database=hubinweb//"
  },
  ```

8. 연결 완료

* * *

# Data DB로 보내기
(이방법 사용하지말고 PowerTool이용)

1. Model 생성

2. Api/*Controller.cs > public class > 아래 줄에 코드 추가
  ```
  private readonly HubinwebContext _context;
  public HomeController(HubinwebContext context)
  {
      _context = context;
  }
  ```

3. Api 코드 추가
  ```
  [HttpPost("PortfoiloPost")]
  public void PortfoiloPost([FromForm] //모델명PortfolioPost// //변수명pp//)
  {
      Portfolio pf = new Portfolio();
      pf.Title = pp.Title;
      pf.Contents = pp.Contents;
      pf.RegDate = DateTime.Now;
      pf.UseYn = "Y";
      pf.Category = pp.Category;

      _context.Add(pf);
      _context.SaveChanges();
  }
  ```

* * *

# PowerTool 이용
1. Controller, ApiController, Index.cshtml, Post.cshtml 복붙

2. 코드 추가, 삭제, 대소문자 확인

3. Controller의 "[Authorize]" 인증? 관련된 것이라 삭제??

4. _Layout.cshtml에 잴 아래 "@"로 시작하는 코드 삭제 (이유는 모르겠음)

5. datatables 라이브러리 삽입

6. _Layout.cshtml에 datatables 라이브러리 관련 코드 추가</br>
  ```
  <link rel="stylesheet" type="text/css" href="/lib/datatables/datatables.min.css" />
  <script type="text/javascript" src="/lib/datatables/datatables.min.js"></script>
  ```

7. wwwroot > js > site.js 에 코드 추가</br>
  ```
  function getDateTime(date) {
    if (date) {
      return moment(date).format('YYYY-MM-DD HH:mm:ss');
    } else {
      return '';
    }
  }

  function getDateTimeForMain(date) {
    if (date) {
      return moment(date).format('YYYY-MM-DD');
    } else {
      return '';
    }
  }
  ```

8. moment 라이브러리 삽입

9. _Layout.cshtml에 moment 라이브러리 관련 코드 추가(위치 중요함)
  ```
  <script src="/lib/moment/moment.min.js"></script>
  ```