from selenium import webdriver
from selenium.webdriver import Keys
from selenium.webdriver.chrome.service import Service
from selenium.webdriver.common.by import By
from selenium.webdriver.support.select import Select

service = Service("./chromedriver.exe")
driver = webdriver.Chrome(service=service)
driver.maximize_window()
driver.get("https://tomspizzeria.b4a.app/")

def siparisver():
    driver.find_element(By.ID, "siparis").click()

def mesajoku():
    return driver.find_element(By.ID, "mesaj").text

#müşteri ismi
siparisver()
mesaj = mesajoku()
assert mesaj == "Müşteri ismi girmediniz"
print(mesaj)

#pizza boyu
isim = "Tom Cruise"
driver.find_element(By.ID,"musteri-adi").send_keys(isim)
siparisver()
mesaj = mesajoku()
assert mesaj == "Pizza boyu seçmediniz"
print(mesaj)

#ödeme şekli
driver.find_element(By.CSS_SELECTOR,"input[value='Küçük']").click()
siparisver()
mesaj = mesajoku()
assert mesaj == "Ödeme tipi seçmediniz"
print(mesaj)

#sipariş alındı
dropdown = driver.find_element(By.ID, "odeme-tipi")
odeme = Select(dropdown)
odeme.select_by_index(2)
siparisver()
mesaj = mesajoku()
assert mesaj == "Siparişiniz alındı"
print(mesaj)

musteri = driver.find_element(By.ID,"musteri").text
boy = driver.find_element(By.ID,"pizzaboyu").text
odeme = driver.find_element(By.ID,"odeme").text

assert musteri == "Müşteri ismi: "+isim
assert boy == "Pizza boyu: Küçük"


#ss alırken ekranı aşağı kaydırma için java kodu insert edicez
driver.execute_script("window.scrollBy(0,150)","")
driver.save_screenshot("./sonuc.png")

#sayfada değişklikler oldu pikseller değişti, sayfanın en altını bulmak için
#driver.execute_script("window.scrollBy(0,document.body.scrollHeight)")
