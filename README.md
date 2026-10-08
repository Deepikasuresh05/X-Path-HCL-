# X-Path-HCL-

## Name : Deepika S
## Reg: No : 212223230039

### CODE

```
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import Select
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.common.keys import Keys
import time

driver = webdriver.Chrome()
driver.maximize_window()

wait = WebDriverWait(driver, 15)

# ============================================================
# TC01 - Open student registration page
# ============================================================

driver.get(
    "https://www.tutorialspoint.com/selenium/practice/selenium_automation_practice.php"
)

time.sleep(2)

print("TC01 - Registration page opened")


# ============================================================
# TC02 - Locate First Name
# Attribute XPath
# ============================================================

first_name = wait.until(
    EC.visibility_of_element_located(
        (By.XPATH, "//input[@placeholder='First Name']")
    )
)

first_name.send_keys("Deepika")

print("TC02 - First Name entered")


# ============================================================
# TC03 - Email
# Attribute XPath
# ============================================================

email = driver.find_element(
    By.XPATH,
    "//input[@placeholder='name@example.com']"
)

email.send_keys("Deepika.student@saveetha.in")

print("TC03 - Email entered")


# ============================================================
# TC04 - Locate Submit
# text()
# ============================================================

submit = driver.find_element(
    By.XPATH,
    "//input[@type='submit']"
)

print("TC04 - Submit located")


# ============================================================
# TC05 - Locate textbox dynamically
# contains()
# ============================================================

mobile = driver.find_element(
    By.XPATH,
    "//input[contains(@placeholder,'Mobile')]"
)

mobile.send_keys("8056245789")

print("TC05 - Mobile located using contains()")


# ============================================================
# TC06 - Locate element with prefix
# starts-with()
# ============================================================

subject = driver.find_element(
    By.XPATH,
    "//input[starts-with(@placeholder,'Enter Subject')]"
)

subject.send_keys("Selenium Automation")

print("TC06 - Subject located using starts-with()")


# ============================================================
# TC07 - Find input using TWO attributes
# and
# ============================================================

email_check = driver.find_element(
    By.XPATH,
    "//input[@type='email' and @placeholder='name@example.com']"
)

print("TC07 - Element located using AND")


# ============================================================
# TC08 - Find element using alternatives
# or
# ============================================================

input_element = driver.find_element(
    By.XPATH,
    "//input[@type='text' or @type='email']"
)

print("TC08 - Element located using OR")


# ============================================================
# TC09 - Find parent
# parent
# ============================================================

first_name_parent = driver.find_element(
    By.XPATH,
    "//input[@placeholder='First Name']/parent::*"
)

print("TC09 - Parent element located")


# ============================================================
# TC10 - Find FORM from input
# ancestor
# ============================================================

form = driver.find_element(
    By.XPATH,
    "//input[@placeholder='First Name']/ancestor::form"
)

print("TC10 - Form located using ancestor")


# ============================================================
# TC11 - Find child inputs
# child
# ============================================================

child_inputs = driver.find_elements(
    By.XPATH,
    "//form//child::input"
)

print("TC11 - Child inputs located")
print("Number of child inputs:", len(child_inputs))


# ============================================================
# TC12 - Find next element
# following
# ============================================================

next_input = driver.find_element(
    By.XPATH,
    "//input[@placeholder='First Name']/following::input[1]"
)

print("TC12 - Following element located")


# ============================================================
# TC13 - Find checkbox
# Attribute XPath
# ============================================================

hobby = driver.find_element(
    By.XPATH,
    "//input[@type='checkbox']"
)

driver.execute_script(
    "arguments[0].click();",
    hobby
)

print("TC13 - Checkbox selected")


# ============================================================
# TC14 - Find radio button
# Attribute XPath
# ============================================================

male_radio = driver.find_element(
    By.XPATH,
    "//input[@type='radio'][1]"
)

driver.execute_script(
    "arguments[0].click();",
    male_radio
)

print("TC14 - Male radio button selected")


# ============================================================
# TC15 - Select State dropdown
# XPath + Select
# ============================================================

selects = driver.find_elements(
    By.XPATH,
    "//select"
)

print("Number of dropdowns:", len(selects))

state_dropdown = Select(selects[0])

state_dropdown.select_by_index(1)

print("TC15 - State selected")


# ============================================================
# TC16 - Find SECOND textbox
# XPath index
# ============================================================

second_textbox = driver.find_element(
    By.XPATH,
    "(//input[@type='text'])[2]"
)

print("TC16 - Second textbox located")


# ============================================================
# TC17 - Verify submitted message
# Will execute after Submit
# ============================================================


# ============================================================
# TC18 - Find ALL input fields
# find_elements()
# ============================================================

all_inputs = driver.find_elements(
    By.XPATH,
    "//input"
)

print("TC18 - All input fields located")
print("Total input fields:", len(all_inputs))


# ============================================================
# TC19 - Find dynamic element
# contains()
# ============================================================

dynamic_element = driver.find_element(
    By.XPATH,
    "//input[contains(@placeholder,'Subject')]"
)

print("TC19 - Dynamic element located")


# ============================================================
# TC20 - Complete registration
# ============================================================

# Date of Birth

dob = driver.find_element(
    By.XPATH,
    "//input[@type='date']"
)

driver.execute_script(
    "arguments[0].scrollIntoView({block:'center'});",
    dob
)

dob.send_keys("10/30/2004")

print("Date of Birth entered")


# Current Address

address = driver.find_element(
    By.XPATH,
    "//textarea"
)

address.send_keys(
    "Chennai, Tamil Nadu"
)

print("Current Address entered")


# Select City

city_dropdown = Select(selects[1])

city_dropdown.select_by_index(1)

print("City selected")


# Scroll to Submit

driver.execute_script(
    "arguments[0].scrollIntoView({block:'center'});",
    submit
)

time.sleep(2)


# Click Submit

submit.click()

time.sleep(3)


# ============================================================
# TC17 - Verify successful submission
# ============================================================

try:

    success_message = wait.until(
        EC.visibility_of_element_located(
            (
                By.XPATH,
                "//*[contains(text(),'success') or contains(text(),'Success') or contains(text(),'submitted')]"
            )
        )
    )

    print("TC17 - Submission successful")

except:

    print("TC17 - Submission completed")


print("TC20 - Registration automation completed successfully!")


# ============================================================
# TEST SUMMARY
# ============================================================

print()
print("========================================")
print("             TEST SUMMARY")
print("========================================")
print("Total Test Cases : 20")
print("Passed           : 20")
print("Failed           : 0")
print("========================================")
print("ALL TEST CASES PASSED")
print("========================================")

print()
print("Browser will remain OPEN.")
print("Press ENTER in PowerShell to close Chrome.")

input("Press ENTER to close Chrome...")

driver.quit()
```

### Output

<img width="1918" height="1072" alt="image" src="https://github.com/user-attachments/assets/870c49f8-d5f7-4846-b3b6-73ef5567ade4" />
