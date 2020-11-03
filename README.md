![header](https://capsule-render.vercel.app/api?type=slice&color=auto&height=130&section=header&text=Selenium%20Webdriver&fontSize=30&fontAlign=80)

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
<br/>
## Example Python script to read Google URL and page title
```
from selenium import webdriver

driver = webdriver.Chrome()
driver.get("https://www.google.com")

print(driver.title)
print(driver.current_url)

driver.quit()
```
<br/>
**Printout:**
 * Google
 * https://www.google.com/

<br/>
### To use webdriver manager

In Command Prompt
```
pip install webdriver-manager
```
<br/>
In Python script
```
    from selenium import webdriver

    from webdriver_manager.chrome import ChromeDriverManager

    driver = webdriver.Chrome(ChromeDriverManager().install())
 ```

![footer](https://capsule-render.vercel.app/api?type=slice&color=auto&height=130&section=footer)
