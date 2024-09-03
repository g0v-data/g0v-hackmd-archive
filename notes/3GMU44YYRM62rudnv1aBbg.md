1. 我的Servicr層
```
public async Task<(bool Success, string Message)> AddQuestionaryAsync(TutorResumeViewModel qVM)
{
    try
    {
        var education = new Education
        {
            SchoolName = qVM.SchoolName,
            StudyStartYear = qVM.StudyStartYear,
            StudyEndYear = qVM.StudyEndYear,
            DepartmentName = qVM.DepartmentName,
            Cdate = DateTime.Now,
            Udate = null
        };
        var member = new Member
        {
            HeadShotImage = qVM.HeadShotImage,
            Cdate = DateTime.Now,
            Udate = null
        };
        var workExperience  = new WorkExperience
        {
            WorkExperienceFile = qVM.WorkExperienceFile,
            WorkStartDate = qVM.WorkStartDate,
            WorkEndDate = qVM.WorkEndDate,
            WorkName = qVM.WorkName,
            Cdate = DateTime.Now,
            Udate = null
        };
        _repository.Create(education);
        _repository.Create(member);
        _repository.Create(workExperience);
        _repository.SaveChanges();

        return (true, "新增資料成功");
    }
    catch (DbUpdateException ex)
    {
        return (false, $"錯誤訊息: {ex.Message}");
    }
}
```
2. 我的viewmodel
```
using Microsoft.AspNetCore.Mvc.Rendering;


namespace Web.ViewModels
{
    public class TutorResumeListViewModel
    {
        public List<TutorResumeViewModel> TutorResumeList { get; set; }
    }


    public class TutorResumeViewModel
    {
        /// <summary>
        /// 大頭貼
        /// </summary>
        //[Required]
        public string HeadShotImage { get; set; }
        /// <summary>
        /// 學校名稱
        /// </summary>
        //[Required]
        public string SchoolName { get; set; }
        /// <summary>
        /// 就學始年
        /// </summary>
        //[Required(ErrorMessage = "請輸入西元年份")]
        public int StudyStartYear { get; set; }
        /// <summary>
        /// 就學結束年
        /// </summary>
        //[Required(ErrorMessage = "請輸入西元年份")]
        public int StudyEndYear { get; set; }
        /// <summary>
        /// 科系名稱
        /// </summary>
        public string DepartmentName { get; set; }
        /// <summary>
        /// 證照
        /// </summary>
        //[Required]
        public List<string> ProfessionalLicenseName { get; set; }
        ///// <summary>
        ///// 證照Url
        ///// </summary>
        ////[Required]
        public List<string> ProfessionalLicenseUrl { get; set; }
        ///// <summary>
        ///// 語言分類
        ///// </summary>
        ////[Required]
        public List<SelectListItem> Category { get; set; }
        ///// <summary>
        ///// 工作起始日期
        ///// </summary>
        ////[Required]
        public DateTime WorkStartDate { get; set; }
        ///// <summary>
        ///// 工作結束日期
        ///// </summary>
        ////[Required]
        public DateTime WorkEndDate { get; set; }
        ///// <summary>
        ///// 工作名稱
        ///// </summary>
        ////[Required]
        public string WorkName { get; set; }
        ///// <summary>
        ///// 工作簡述檔案
        ///// </summary>
        ////[Required(ErrorMessage = "請上傳檔案")]
        public string WorkExperienceFile { get; set; }
    }
}

```
我的entity分別為
```
using System;
using System.Collections.Generic;

namespace Web.Entities;

public partial class Education
{
    /// <summary>
    /// 學歷Id
    /// </summary>
    public int EducationId { get; set; }

    /// <summary>
    /// 學校名稱
    /// </summary>
    public string SchoolName { get; set; }

    /// <summary>
    /// 在學期間起
    /// </summary>
    public int StudyStartYear { get; set; }

    /// <summary>
    /// 在學期間迄
    /// </summary>
    public int StudyEndYear { get; set; }

    /// <summary>
    /// 科系名稱
    /// </summary>
    public string DepartmentName { get; set; }

    /// <summary>
    /// 建立時間
    /// </summary>
    public DateTime Cdate { get; set; }

    /// <summary>
    /// 修改時間
    /// </summary>
    public DateTime? Udate { get; set; }

    public virtual ICollection<Member> Members { get; set; } = new List<Member>();
}

```

```
using System;
using System.Collections.Generic;

namespace Web.Entities;

public partial class Member
{
    /// <summary>
    /// 會員Id
    /// </summary>
    public int MemberId { get; set; }

    /// <summary>
    /// 會員頭像
    /// </summary>
    public string HeadShotImage { get; set; }

    /// <summary>
    /// 國籍Id
    /// </summary>
    public int? NationId { get; set; }

    /// <summary>
    /// 優質會員
    /// </summary>
    public bool IsVerifiedTutor { get; set; }

    /// <summary>
    /// 名字
    /// </summary>
    public string FirstName { get; set; }

    /// <summary>
    /// 姓氏
    /// </summary>
    public string LastName { get; set; }

    /// <summary>
    /// 密碼
    /// </summary>
    public string Password { get; set; }

    /// <summary>
    /// 電子郵件信箱
    /// </summary>
    public string Email { get; set; }

    /// <summary>
    /// 綽號
    /// </summary>
    public string Nickname { get; set; }

    /// <summary>
    /// 電話
    /// </summary>
    public string Phone { get; set; }

    /// <summary>
    /// 生日
    /// </summary>
    public DateTime? Birthday { get; set; }

    /// <summary>
    /// 性別
    /// </summary>
    public short Gender { get; set; }

    /// <summary>
    /// 母語
    /// </summary>
    public string NativeLanguage { get; set; }

    /// <summary>
    /// 會的語言
    /// </summary>
    public string SpokenLanguage { get; set; }

    /// <summary>
    /// 銀行代碼
    /// </summary>
    public string BankCode { get; set; }

    /// <summary>
    /// 帳戶名稱
    /// </summary>
    public string BankAccount { get; set; }

    /// <summary>
    /// 最高學歷Id
    /// </summary>
    public int? EducationId { get; set; }

    /// <summary>
    /// 教師自介
    /// </summary>
    public string TutorIntro { get; set; }

    /// <summary>
    /// 帳號
    /// </summary>
    public string Account { get; set; }

    /// <summary>
    /// 帳號類型
    /// </summary>
    public int AccountType { get; set; }

    /// <summary>
    /// 建立時間
    /// </summary>
    public DateTime Cdate { get; set; }

    /// <summary>
    /// 更新時間
    /// </summary>
    public DateTime? Udate { get; set; }

    /// <summary>
    /// 是否為教師
    /// </summary>
    public bool IsTutor { get; set; }

    public virtual ICollection<ApplyList> ApplyLists { get; set; } = new List<ApplyList>();

    public virtual ICollection<Booking> Bookings { get; set; } = new List<Booking>();

    public virtual Education Education { get; set; }

    public virtual ICollection<MemberPreference> MemberPreferences { get; set; } = new List<MemberPreference>();

    public virtual Nation Nation { get; set; }

    public virtual ICollection<Order> Orders { get; set; } = new List<Order>();

    public virtual ICollection<ProfessionalLicense> ProfessionalLicenses { get; set; } = new List<ProfessionalLicense>();

    public virtual ICollection<Review> Reviews { get; set; } = new List<Review>();

    public virtual ICollection<ShoppingCart> ShoppingCarts { get; set; } = new List<ShoppingCart>();

    public virtual ICollection<TutorTimeSlot> TutorTimeSlots { get; set; } = new List<TutorTimeSlot>();

    public virtual WatchList WatchList { get; set; }

    public virtual ICollection<WorkExperience> WorkExperiences { get; set; } = new List<WorkExperience>();
}

```

```
using System;
using System.Collections.Generic;

namespace Web.Entities;

public partial class WorkExperience
{
    /// <summary>
    /// 工作經驗Id
    /// </summary>
    public int WorkExperienceId { get; set; }

    /// <summary>
    /// 工作經驗檔案路徑
    /// </summary>
    public string WorkExperienceFile { get; set; }

    /// <summary>
    /// 工作起始日
    /// </summary>
    public DateTime WorkStartDate { get; set; }

    /// <summary>
    /// 工作結束日
    /// </summary>
    public DateTime WorkEndDate { get; set; }

    /// <summary>
    /// 工作經驗名稱
    /// </summary>
    public string WorkName { get; set; }

    /// <summary>
    /// 會員Id
    /// </summary>
    public int MemberId { get; set; }

    /// <summary>
    /// 建立時間
    /// </summary>
    public DateTime Cdate { get; set; }

    /// <summary>
    /// 修改時間
    /// </summary>
    public DateTime? Udate { get; set; }

    public virtual Member Member { get; set; }
}

```

"我的問題 我的service曾有錯誤嗎 表單無法寫入資料庫"