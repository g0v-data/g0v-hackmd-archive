1. 我的service
''' public async Task<(bool Success, string Message)> AddQuestionaryAsync(TutorResumeViewModel qVM)
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
}'''