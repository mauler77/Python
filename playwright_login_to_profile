from playwright.sync_api import sync_playwright
import time
import random
import os

login = "aaaaa"
password = "aaaaa"
USER_DATA_DIR = "/Users/halid/PlaywrightProfiles/InstagramProfile"

def random_delay(min_sec=0.7, max_sec=2.3):
    return int(random.uniform(min_sec, max_sec)*1000)

if not os.path.exists(USER_DATA_DIR):
    os.makedirs(USER_DATA_DIR)

with sync_playwright() as p:
    browser_context = p.chromium.launch_persistent_context(
        USER_DATA_DIR,
        headless=False,
        viewport={"width": 1280, "height": 800},
        user_agent="Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/115.0 Safari/537.36"
    )
    page = browser_context.new_page()

    page.goto("https://instagram.com/accounts/login/")

  
    try:
        page.wait_for_selector('input[name="username"]', timeout=10000)
        page.wait_for_selector('input[name="password"]', timeout=10000)

        logins = page.locator('input[name="username"]')
        passwords = page.locator('input[name="password"]')

        logins.click()
        logins.press_sequentially(login, delay=random_delay())
        passwords.click()
        passwords.press_sequentially(password, delay=random_delay())
        page.click('button[type="submit"]')

        random_delay(5, 8)
    except:
        print("Похоже, вы уже залогинены или поля ввода не появились.")

    print("Вход выполнен или уже был выполнен ранее.")
    print("Скрипт будет ждать 300 секунд перед закрытием браузера.")
    time.sleep(300)

    browser_context.close()
