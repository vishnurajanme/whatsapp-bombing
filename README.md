# whatsapp-bombing using selenium
Most simple code for whatsapp bombing using browser automation with selenium with support for searching and finding people and
sending n number of messages to them
1. Install selenium
```python
pip install selenium
```
2. Considering we have already installed the chrome driver for selenium,importing the driver and setting arguments
```python
from selenium import webdriver 
from selenium.webdriver.support.ui import WebDriverWait 
from selenium.webdriver.support import expected_conditions as EC 
from selenium.webdriver.common.keys import Keys 
from selenium.webdriver.common.by import By 
```
3. Taking name of people you want to send message too and the message itself as input
```python
#name
names = input("Enter the message recipient's names separated by space").split()
# message
string = input("Enter the message you want to send")
```
4. Setting the chromedriver path, opening website etc.
```python
#chrome driver path
driver = webdriver.Chrome('/Users/vishnurajan/Documents/chromedriver') 
#opening website
driver.get("https://web.whatsapp.com/")
# delay
wait = WebDriverWait(driver, 600) 
```
5. Searching and finding the elements in whatsapp web so as to send message. Step 1: Finding the search box and searching name
Step2: Finding the messagebox, type the message and hit enter to send the message. Repeat this for all nams and n number of times
```python
for i in range(len(names)):

    # Searching with name
    search_box= wait.until(EC.presence_of_element_located((By.XPATH, '//*[@id="side"]/div[1]/div/label/div/div[2]'))) 
    search_box.send_keys(names[i] + Keys.ENTER)
    
    # Sending mesaage
    input_box = driver.find_element_by_xpath('//*[@id="main"]/footer/div[1]/div[2]/div/div[2]')
    for i in range(2):
        input_box.send_keys(string + Keys.ENTER)
```
