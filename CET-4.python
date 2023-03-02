#利用百度ocr识别自动登陆四级考试网并进入报名页面
from selenium import webdriver
from time import sleep
from PIL import Image
from aip import AipOcr
from selenium.webdriver.support.select import Select
from selenium.common.exceptions import UnexpectedAlertPresentException
import time

#驱动的加载和访问页面
driver = webdriver.Firefox()
driver.maximize_window()
#设置页面加载时间
driver.set_page_load_timeout(80)
driver.set_script_timeout(30)
#CET-考试系统网址
url = 'https://passport.neea.edu.cn/CETLogin?ReturnUrl=http://cet-bm.neea.edu.cn/Home/VerifyPassport/?LoginType=0'
driver.get(url)

#点击进入报名页面

#填写相关信息

username = '***' #这里填写你的登陆用户名，如手机号
password = '***'  #这里输入你的登陆密码
#选择省份
selectA = driver.find_element_by_id("selectProvince")
select = Select(selectA)
select.select_by_value("44")
#输入账号与密码
driver.find_element_by_id("txtUserName").send_keys(username)
driver.find_element_by_id("txtPassword").send_keys(password)
time.sleep(5)
driver.implicitly_wait(10)
#点击登录
driver.find_element_by_xpath("//button[@id='ibtnLogin']").click()
driver.switch_to.alert.accept()
driver.implicitly_wait(3)

##进入页面的操作
driver.find_element_by_xpath("//a[@class='zc_button']").click()
driver.switch_to.alert.accept()
driver.find_element_by_id("btnEditSReg").click()
try:
    driver.find_element_by_xpath("//span[@class='box']").click()
    driver.find_element_by_xpath("//a[@id='btnSearch']").click()
    count = 0
except Exception:
    pass
while True:
    try:
        time.sleep(1)
        driver.refresh()
        driver.switch_to.alert.accept()
        driver.find_element_by_xpath("//span[@class='box']").click()
        driver.find_element_by_xpath("//a[@id='btnSearch']").click()
        count = count+1
        print(count)
        driver.switch_to.alert.accept()
    except Exception as err:
        print(err)



