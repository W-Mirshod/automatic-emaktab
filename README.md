# automatic-emaktab
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
import time

# list of (username, password) tuples
accounts = [
    ("username1", "password1"),
    ("username2", "password2"),
    # Add up to 30
]

# change to your chromedriver path if needed
driver_path = "chromedriver"

# change to your login URL if it changes
login_url = "https://login.emaktab.uz/"

for uname, pwd in accounts:
    driver = webdriver.Chrome(driver_path)
    driver.get(login_url)
    time.sleep(2)  # let page load

    # change selectors if the site changes
    driver.find_element(By.NAME, "username").send_keys(uname)
    driver.find_element(By.NAME, "password").send_keys(pwd)
    driver.find_element(By.XPATH, "//button[@type='submit']").click()  # adjust if needed

    time.sleep(3)  # wait for login
    # do something after login, e.g., check login status, scrape, etc.

    driver.quit()
