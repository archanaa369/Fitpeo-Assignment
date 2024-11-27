import time
from selenium import webdriver
from selenium.webdriver.common.action_chains import ActionChains
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.support.ui import WebDriverWait

slider_target_value = 820
text_Field_value = 560
Total_Recurring_Reimbursement='$110700'

global slider
global text_field

# Initialize WebDriver
driver = webdriver.Chrome()
driver.maximize_window()
action = ActionChains(driver)


def case1():
    try:
        driver.get("https://fitpeo.com")  # Replace with the actual URL of FitPeo homepage
        print("TestCase 1: Pass Navigated to FitPeo Homepage Pass")
    except Exception as e:
        print("TestCase 1: Fail Navigated to FitPeo Homepage Failed")
        print(e)



def case2():
    try:
        # TestCase 2: Navigate to the Revenue Calculator Page
        revenue_calculator_link = WebDriverWait(driver, 10).until(EC.presence_of_element_located((By.LINK_TEXT, "Revenue Calculator")))  # Adjust locator as needed
        revenue_calculator_link.click()
        print("TestCase 2: Pass Navigated to the Revenue Calculator Page")
    except Exception as e:
        print("TestCase 2: Pass Navigated to the Revenue Calculator Page")
        print(e)



def case3():
    try:
        # TestCase 3: Scroll Down to the Slider Section
        global slider
        slider = WebDriverWait(driver, 10).until(EC.presence_of_element_located((By.CSS_SELECTOR,'input[type="range"][data-index="0"]'))) # Adjust selector if needed
        driver.execute_script("arguments[0].scrollIntoView(true);", slider)
        time.sleep(2)  # Wait for smooth scrolling
        print("TestCase 3: Pass Scrolled down to the Slider section")
    except Exception as e:
        print("TestCase 3: Fail Scrolled down to the Slider section")
        print(e)


def case4():
    try:
        # TestCase 4: Adjust the slider to set its value to 820
        action.click_and_hold(slider).move_by_offset(93, 0).release().perform()
        time.sleep(1)
        action.click_and_hold(slider).send_keys(Keys.ARROW_RIGHT * 3).release().perform()
        time.sleep(2)
        slider_field_Value = slider.get_property("value")
        if slider_field_Value == str(slider_target_value):
            print(f"TestCase 4: Pass Slider value updated to {slider_field_Value}")
        else:
            print(f"TestCase 4: Fail Expected {slider_target_value}, but got {slider_field_Value}")
    except Exception as e:
        print("TestCase 4: Failed Adjust the slider to set its value to 820")
        print(e)


def case5():
    try:
        # TestCase 5: Update the Text Field value 560
        global text_field
        text_field = WebDriverWait(driver, 10).until(EC.presence_of_element_located((By.CSS_SELECTOR, 'input[type="number"]')))
        ActionChains(driver).click(text_field).send_keys(Keys.BACKSPACE * 3).perform()
        ActionChains(driver).click(text_field).send_keys(str(text_Field_value)).perform()
        print("TestCase 5: Pass Update the Text Field value {text_Field_value}")
    except Exception as e:
        print("TestCase 5: Failed Update the Text Field value {text_Field_value}")
        print(e)


def case6():
    try:
        slider_Validate = slider.get_property('value')
        if slider_Validate == str(text_Field_value):
            print(f"TestCase 6: Pass Validate: Slider value updated to {text_Field_value}")
        else:
            print(f"TestCase 6: Fail Validate: Expected slider Value{text_Field_value}, but got {slider_Validate}")

        time.sleep(4)
        ActionChains(driver).click(text_field).send_keys(Keys.BACKSPACE * 3).perform()
        ActionChains(driver).click(text_field).send_keys(str(slider_target_value)).perform()
        time.sleep(2)
    except Exception as e:
        print("TestCase 6: Failed Validate Slider Value value 560")
        print(e)


def case7():
    try:
        # TestCase 7: Select CPT Codes
        driver.find_element(By.XPATH, "(//input[@type='checkbox'])[1]").click()
        time.sleep(1)
        driver.find_element(By.XPATH, "(//input[@type='checkbox'])[2]").click()
        time.sleep(1)
        driver.find_element(By.XPATH, "(//input[@type='checkbox'])[3]").click()
        time.sleep(1)
        driver.find_element(By.XPATH, "(//input[@type='checkbox'])[8]").click()
        time.sleep(2)
        finalTotal = driver.find_element(By.XPATH,"//*[@class='MuiToolbar-root MuiToolbar-gutters MuiToolbar-regular css-1lnu3ao']/p[4]/p").text
        if finalTotal == Total_Recurring_Reimbursement:
            print(
                f"TestCase 7: Pass Validate: Total Recurring Reimbursement value updated to {Total_Recurring_Reimbursement}")
        else:
            print(
                f"TestCase 7: Fail Validate: Expected Total Recurring Reimbursement value{Total_Recurring_Reimbursement}, but got {finalTotal}")
    except Exception as e:
        print("TestCase 7: Failed Select CPT Codes")
        print(e)


def main():
    case1()
    case2()
    case3()
    case4()
    case5()
    case6()
    case7()
    time.sleep(5)


if __name__=='__main__':
    main()
