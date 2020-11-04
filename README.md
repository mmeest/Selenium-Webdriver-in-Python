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
<img src="chrome.jpg" widht="50px">
**Chrome driver:** https://chromedriver.chromium.org/downloads
<img src="edge.jpg" widht="50px">
**Edge driver:** https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/
<img src="fox.jpg" widht="50px">
**Firefox driver:** https://github.com/mozilla/geckodriver/releases
<img src="safari.jpg" widht="50px">
**Safari driver:** https://webkit.org/blog/6900/webdriver-support-in-safari-10/

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
## Dropdowns
To use dropdown with id and values

```
from selenium import webdriver

class Dropdown:
    def __init__(self, driver, dropdown_id):
        self.driver = driver
        self.dropdown_id = dropdown_id
        self.dropdown = driver.find_element_by_id(dropdown_id)

    def select(self, value):
        self.dropdown.click()
        self.driver.find_element_by_xpath("//select[@id = '{}']/option[text() = '{}']".format(self.dropdown_id, value))
        return self

    def get_selected(self):
        return str(self.driver.find_element_by_xpath("//select[@id = '{}']/option[@selected]").text)

    def is_selected(self, value):
        return value == self.get_selected()

    def get_avaliable_selections(self):
        data = []
        xpath = "//select[@id = '{}'/option".format(self.dropdown_id)
        count = len(self.driver.find_elements_by_xpath(xpath))
        for index in range(1, count + 1):
            data.append(self.driver.find_element_by_xpath("{}[{}]".format(xpath, index)).text)
        return data

if "__main__" == __name__:

    driver = webdriver.Chrome()
    driver.get("https://www.travelocity.com/#")

    rooms = Dropdown(driver, "package-rooms-hp-package")
    adults = Dropdown(driver, "package-l-adults-hp-pacage")
    children = Dropdown(driver, "package-l-children-hp-package")
    preferred_class = Dropdown(driver, "package-advanced-preferred-class-hp-package")

    dropdowns = [rooms, adults, children, preferred_class]
    for dropdown in dropdowns:
        print dropdown.get_selected()
        print dropdown.is_selected(1)
        print dopdown.get_avaliable_selections[]
        dropdown.select("2")
```

&nbsp;
## Radio Buttons
* Example code:
```
from selenium import webdriver

class RadioButton:

    def __init__(self, driver, text):

        self.driver = driver
        self.text = text
        self.button = self.driver.find_element_by_xpath("//button[contains(@class, 'btn btnLrg btnSecondary') "
                                                        "and text() = '{}']".format(text))

    def is_selected(self):

        return "btnSelected" in self.button.get_attribute("class")

    def select(self):

        self.button.click()
        return self

class RadioButtonGroup:

    def __init__(self, radio_buttons):

        self.radio_buttons = radio_buttons

    def get_selected(self):

        for radio_button in self.radio_buttons:
            if radio_button.is_selected():
                return radio_button.text 

if "__main__" == __name__:

    driver = webdriver.Chrome()
    driver.get("https://www.travelocity.com/#")

    buy = RadioButton(driver, "Buy")
    rent = RadioButton(driver, "Rent")
    sold = RadioButton(driver, "Sold")

    group = RadioButtonGroup([buy, rent, sold])
    print(group.get_selected())

    buy.select()
    print(group.get_selected())

    rent.select()
    print(group.get_selected())
    
```
**Printout:**\
* Buy\
* Buy\
* Rent\
* Sold

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
