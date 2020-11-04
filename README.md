![header](https://capsule-render.vercel.app/api?type=slice&color=auto&height=130&section=header&text=Selenium%20Webdriver&fontSize=30&fontAlign=80)

<img src="https://selenium-python.readthedocs.io/_static/logo.png" width="100px">
https://selenium-python.readthedocs.io/index.html

# Selenium-Webdriver-in-Python

## Install Selenium in Pyhton
```
pip install selenium
```
or for python3
```
pip3 install selenium
```
&nbsp;
## Webdrivers
* Chrome driver: https://chromedriver.chromium.org/downloads

1. Download matching version of your Chrome browser.
2. Extract chromedriver.exe for example to C:/webdrivers
3. Add chromedriver system PATH:
  **Win > Computer > Properties > Advanced system settings > Environment Variables > System variables > Path**

&nbsp;
## Example Python script to read Google URL and page title
```
from selenium import webdriver

driver = webdriver.Chrome()
driver.get("https://www.google.com")

print(driver.title)
print(driver.current_url)

driver.quit()
```

&nbsp;
**Printout:**
 * Google
 * https://www.google.com/
 
 
&nbsp;
## Select element by
* by ID:
```
driver.find_element(By.ID, "id_name")
```
* to pass text(abc) to the textfield using textfield ID('user_input')
```
driver.find_element(By.ID, "user_input").send_keys("abc")
```
* to print out element src attribute
```
print driver.find_element(By.ID, "logo").get_attribute("src")
```
* to print out text from DOM element(button name="btnK")
```
print driver.find_element(By.NAME, "btnK").get_attribute("value")
```
* to click on button
```
driver.find_element(By.NAME, "btnK").click()
```
&nbsp;
*find_element_by_id*\
*find_element_by_name*\
*find_element_by_xpath*\
*find_element_by_link_text*\
*find_element_by_partial_link_text*\
*find_element_by_tag_name*\
*find_element_by_class_name*\
*find_element_by_css_selector*

&nbsp;
**To find multiple elements (these methods will return a list):**\
&nbsp;
*find_elements_by_name*\
*find_elements_by_xpath*\
*find_elements_by_link_text*\
*find_elements_by_partial_link_text*\
*find_elements_by_tag_name*\
*find_elements_by_class_name*\
*find_elements_by_css_selector*
&nbsp;

## To use keyboard keys
* to push **'Enter'** key on element:
```
from selenium.webdriver.common.keys import Keys
driver.find_element_by_name("Value").send_keys(Keys.RETURN)
```

OR

```
driver.find_element_by_name("Value").send_keys(Keys.ENTER)
```

OR

```
element = driver.find_element_by_id("Value")
element.send_keys("keysToSend")
element.submit()
```

&nbsp;

## XPATH
<img src="https://lh3.googleusercontent.com/j4P-AWd7yeu0r6Od7XkcrmlR80rM5KLiyUx2LWcX3r9vdQTFEWtuKD9iSg_9Pwuw2ZfR2QsW6p4=w128-h128-e365-rj-sc0x00ffffff" width="100px">
XPATH Helper Wizard for Google Chrome by Data-Miner.io:\
https://chrome.google.com/webstore/detail/xpath-helper-wizard/jadhpggafkbmpdpmpgigopmodldgfcki
&nbsp;
XPath Axes and their Shortcuts:\
https://our.umbraco.com/documentation/reference/templating/macros/xslt/xpath-axes-and-their-shortcuts
&nbsp;
<img src="https://our.umbraco.com/documentation/reference/templating/macros/xslt/Images/7x1B0.gif" alt="XPATH">

&nbsp;
### To use webdriver manager

In Command Prompt
```
pip install webdriver-manager
```

&nbsp;
In Python script
```
    from selenium import webdriver

    from webdriver_manager.chrome import ChromeDriverManager

    driver = webdriver.Chrome(ChromeDriverManager().install())
 ```

![footer](https://capsule-render.vercel.app/api?type=slice&color=auto&height=130&section=footer)
