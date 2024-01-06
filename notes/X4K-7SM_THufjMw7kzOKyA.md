Note: Please do not remove the indentation. 
請不要修改縮進

-- APP.yaml --
vaccineAvailability:
  en: Vaccine Availability
  zh: 疫苗資訊
  th: สถานะของวัคซีน
  id: Ketersediaan Vaksin
  jp: 新型コロナワクチン情報
vaccineTypes:
  governmentPaid:
    en: Government-Paid Vaccinations
    zh: 公費疫苗
    th: รัฐบาลสนับสนุนค่าใช้จ่าย
    id: Vaksinasi dibiayai pemerintah
    jp: ワクチン接種（公費負担）
  selfPaid:
    en: Self-Paid Vaccinations
    zh: 自費疫苗
    th: รับผิดชอบค่าใช้จ่ายด้วยตนเอง
    id: Vaksinasi dibiayai probadi
    jp: ワクチン接種（自費負担）
websiteTitle:
  en: COVID-19 Vaccination Information
  zh: 全民新冠肺炎 (COVID-19) 疫苗資訊
  th: ข้อมูลวัคซีนป้องกัน COVID-19
  id: Informasi Vaksinasi COVID-19
  jp: 新型コロナワクチン情報

-- Card.yaml --
availability:
  available:
    en: Available
    zh: 有名額
    th: ว่าง
    id: Tersedia
  unavailable:
    en: Unavailable
    zh: 無名額
    th: ไม่ว่าง
    id: Tidak Tersedia
    jp: 空きあり
  noData:
    en: No Data
    zh: 無資訊
    th: ไม่มีข้อมูล
    id: Tidak ada data
    jp: 情報はありません
locations:
  keelung:
    en: Keelung City
    zh: 基隆市
    th: เมืองจีหลง
    id: Kota Keelung
    jp: 基隆市
  taipei:
    en: Taipei City
    zh: 臺北市
    th: เมืองไทเป
    id: Kota Taipei
    jp: 台北市
  newTaipeiCity:
    en: New Taipei City
    zh: 新北市
    th: เมืองนิวไทเป
    id: Kota Taipei Baru
    jp: 新北市
  taoyuan:
    en: Taoyuan City
    zh: 桃園市
    th: เมืองเถาหยวน
    id: Kota Taoyuan
    jp: 桃園市
  hsinchuCounty:
    en: Hsinchu County
    zh: 新竹縣
    th: ซินจู๋
    id: Kabupaten Hsinchu
    jp: 新竹県
  hsinchuCity:
    en: Hsinchu City
    zh: 新竹市
    th: เมืองซินจู๋
    id: Kota Hsinchu
    jp: 新竹市
  miaoli:
    en: Miaoli County
    zh: 苗栗縣
    th: เหมี่ยวลี่
    id: Kabupaten Miaoli
    jp: 苗栗県
  yilan:
    en: Yilan County
    zh: 宜蘭縣
    th: อี๋หลัน
    id: Kabupaten Yilan
    jp: 宜蘭県
  taichung:
    en: Taichung City
    zh: 臺中市
    th: เมืองไทจง
    id: Kota Taichung
    jp: 台中市
  yunlin:
    en: Yunlin County
    zh: 雲林縣
    th: อวิ๋นหลิน
    id: Kabupaten Yunlin
    jp: 雲林県
  changhua:
    en: Changhua County
    zh: 彰化縣
    th: จางฮั่ว
    id: Kabupaten Changhua
    jp: 彰化県
  nantou:
    en: Nantou County
    zh: 南投縣
    th: หนานโถว
    id: Kabupaten Nantou
    jp: 南投県
  chiayi:
    en: Chiayi County
    zh: 嘉義縣
    th: เจียอี้
    id: Kabupaten Chiayi
    jp: 嘉義県
  tainan:
    en: Tainan City
    zh: 臺南市
    th: เมืองไถหนาน
    id: Kabupaten Tainan
    jp: 台南市
  kaohsiung:
    en: Kaohsiung City
    zh: 高雄市
    th: เมืองเกาสง
    id: Kota Kaohsiung
    jp: 高雄市
  pingtung:
    en: Pingtung County
    zh: 屏東縣
    th: ผิงตง
    id: Kabupaten Pingtung
    jp: 屏東県
  hualien:
    en: Hualien County
    zh: 花蓮縣
    th: ฮัวเหลียน
    id: Kabupaten Hualien
    jp: 花蓮県
  lienjiang:
    en: Lienjiang County
    zh: 連江縣
    th: เหลียนเจียง
    id: Kabupaten Lienjiang
    jp: 連江県
  penghu:
    en: Penghu County
    zh: 澎湖縣
    th: เผิงหู
    id: Kabupaten Penghu
    jp: 澎湖県
  taitung:
    en: Taitung County
    zh: 臺東縣
    th: ไถตง
    id: Kabupaten Taitung
    jp: 台東県
  kinmen:
    en: Kinmen County
    zh: 金門縣
    th: จินเหมิน
    id: Kabupaten Kinmen
    jp: 金門県

-- VaccineDataGrid.yaml --
---
hospitalsWithAppointmentsTitle:
  en: Hospitals with Available Appointments
  zh: 有名額的醫院
  th: โรงพยาบาลที่สามารถนัดหมายเวลาได้
  id: Rumah sakit dengan janji temu
  jp: 接種枠ある医療機関
hospitalsWithAppointmentsSubtitle:
  governmentPaid:
    en: We have confirmed that appointments are available at these hospitals.
    zh: 我們已確認該醫院有公費疫苗接種名額
    th: เราได้ทำการยืนยันแล้วว่าท่านสามารถทำการนัดหมายเวลาเพื่อฉีดวัคซีนที่โรงพยาบาลเหล่านี้ได้
    id: Kami telah mengkonfirmasi janji temu tersedia pada rumah sakit berikut
    jp: こちらの医療機関は公費接種枠がある事を確認できました。
  selfPaid:
    en: We have confirmed that appointments are available at these hospitals.
    zh: 我們已確認該醫院有自費疫苗接種名額
    th: เราได้ทำการยืนยันแล้วว่าท่านสามารถทำการนัดหมายเวลาเพื่อฉีดวัคซีนที่โรงพยาบาลเหล่านี้ได้
    id: Kami telah mengkonfirmasi janji temu tersedia pada rumah sakit berikut
    jp:こちらの医療機関は自費接種枠がある事を確認できました。
hospitalsWithNoDataTitle:
  en: Hospitals with No Data
  zh: 無資訊的醫院
  th: ไม่มีข้อมูลของโรงพยาบาล
  id: Rumah sakit tanpa data
  jp: こちらの医療機関はワクチン接種に関する情報はございません。
hospitalsWithNoDataSubtitle:
  governmentPaid:
    en: We are unable to confirm if appointments are available at these hospitals. Please check their websites for more information.
    zh: 我們無法確認該醫院的公費疫苗接種名額。請查看醫院的官網。
    th: เราไม่สามารถตรวจสอบได้ว่าโรงพยาบาลเหล่านี้สามารถทำการนัดหมายเวลาเพื่อฉีดวัคซีนได้ กรุณาตรวจสอบเว็บไซต์ของโรงพยาบาล
    id: Kami tidak tahu apakah rumah sakit ini memiliki janji temu. Silakan periksa situs web rumah sakit.
    jp: こちらの医療機関はワクチン接種（公費）に関する情報はございません。
  selfPaid:
    en: We are unable to confirm if appointments are available at these hospitals. Please check their websites for more information.
    zh: 我們無法確認該醫院的自費疫苗接種名額。請查看醫院的官網。
    th: เราไม่สามารถตรวจสอบได้ว่าโรงพยาบาลเหล่านี้สามารถนัดหมายเวลาเพื่อฉีดวัคซีนได้ กรุณาตรวจสอบเว็บไซต์ของโรงพยาบาล
    id: Kami tidak tahu apakah rumah sakit ini memiliki janji temu. Silakan periksa situs web rumah sakit.
    jp: こちらの医療機関はワクチン接種（自費）に関する情報はございません。
hospitalsWithNoAppointmentsTitle:
  zh: 無名額的醫院
  en: Hospitals with No Appointments
  th: โรงพยาบาลที่ไม่สามารถนัดหมายเวลาได้
  id: Rumah sakit tanpa janji temu
  jp: こちらの医療機関はワクチン接種の枠がございません。
hospitalsWithNoAppointmentsSubtitle:
  governmentPaid:
    en: There are no available appointments at these hospitals. Please check again later.
    zh: 這些醫院沒有公費疫苗接種名額。請稍後再查詢本網站
    th: โรงพยาบาลเหล่านี้ไม่สามารถทำการนัดหมายเวลาเพื่อฉีดวัคซีนได้ กรุณาทำการตรวจสอบใหม่อีกครั้ง
    id: Janji temu pada rumah sakit ini tidak tersedia. Silahkan periksa lagi nanti.
    jp: こちらの医療機関はワクチン接種（公費）の枠がございません。
  selfPaid:
    en: There are no available appointments at these hospitals. Please check again later.
    zh: 這些醫院沒有自費疫苗接種名額。請稍後再查詢本網站
    th: โรงพยาบาลเหล่านี้ไม่สามารถทำการนัดหมายเวลาเพื่อฉีดวัคซีนได้ กรุณาทำการตรวจสอบใหม่อีกครั้ง
    id: Janji temu pada rumah sakit ini tidak tersedia. Silahkan periksa lagi nanti.
    jp: こちらの医療機関はワクチン接種（自費）の枠がございません。
noHospitals:
  en: No hospitals within this category.
  zh: 該種類無醫院
  th: ไม่มีข้อมูลโรงพยาบาลในหมวดหมู่นี้
  id: Tidak ada rumah sakit dalam kategori ini
  jp: こちらのカテゴリには、医療機関がございません。
buttons:
  getAppointment:
    en: Make an Appointment
    zh: 前往醫院官網掛號
    th: ไปที่เว็บไซต์ของโรงพยาบาลเพื่อทำการนัดหมาย
    id: Dapatkan janji temu
    jp: 医療機関の公式ホームページからご予約ください
  visitWebsite:
    en: Visit Hospital Website
    zh: 前往醫院官網查詢
    th: ไปที่เว็บไซต์ของโรงพยาบาล
    id: Kunjungi situs web rumah sakit
    jp: 医療機関の公式ホームページよりご確認ください
