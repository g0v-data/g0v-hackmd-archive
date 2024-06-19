# React 雙重map陣列迴圈應用

<h2>使用要點</h2>
<p>當json有兩層資料，在迴圈第一層資料後在迴圈第二層資料，適合用在判定縣市後再選擇鄉鎮</p>

code如下
```
import twCity from "@/public/TaiwanAddressCityAreaRoadChineseEnglishJSON-master/CityCountyData.json";

 const twCity = useState([
        {
            "CityName": "連江縣",
            "CityEngName": "Lienchiang County",
            "AreaList": [
                { "ZipCode": "209", "AreaName": "南竿鄉", "AreaEngName": "Nangan Township" },
                { "ZipCode": "210", "AreaName": "北竿鄉", "AreaEngName": "Beigan Township" }
            ]
        }
        ])

const[city, setCity] = useState("")
  const[county,setCounty] =useState([])
  const handleCity=(e) => {
    const selectCity=(e.target.value)   ///從option回傳數值
    
    setCity(selectCity) ///確定了city數值
    
    const cityData = twCity.find((v) =>  
        v.CityName === selectCity) ///定義cityData= 在twCity.json檔案中cityName與city相等的資料
        
        
    console.log(cityData.AreaList)
    if(cityData){
        setCounty(cityData.AreaList)
        console.log(county)
    } ///若有cityData這個值時 setCounty會等於資料的AreaList的資料
  }
  ```
  喧染code如下
  ```
  retrun(
  
            <div className="d-flex register-city ">
            <div className="register-county form-floating" style={{width:"220px"}}>
              <select class="form-select" aria-label="Default select example" onChange={handleCity}>
                <option selected>請選擇縣市</option>
                {twCity.map((v, i) => {
                  return <option key={i} >{v.CityName} </option>;
                })}
              </select>
              <label for="floatingInputValue">請選擇縣市</label>
            </div>
            <div className=" ms-5 register-county form-floating" style={{width:"220px"}}>
              <select class="form-select" aria-label="Default select example">
              <option selected>請選擇區/鎮</option>
              {Array.isArray(county) && county.map((v, i) => (
                        <option key={i} value={v.AreaName}>{v.AreaName}</option>
                    ))} 
                
              </select>
              <label for="floatingInputValue">請選擇區/鎮</label>
            </div>
          </div>
        </div>)
```
{Array.isArray(county)判定county是否為陣列