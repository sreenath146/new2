# new2
initial update
this is sreenath


list = []
list2 = []
driver = webdriver.Chrome(executable_path="C:\\chromedriver.exe")
driver.get("https://rahulshettyacademy.com/seleniumPractise/#/")
driver.find_element_by_css_selector("input.search-keyword").send_keys("ber")
time.sleep(3)
count = len(driver.find_elements_by_xpath("//div[@class='products']/div"))
assert count == 3
buttons = driver.find_elements_by_xpath("//div[@class='product-action']/button")

for button in buttons:
    list.append(button.find_element_by_xpath("parent::div/parent::div/h4").text)
    button.click()
print(list)

driver.find_element_by_css_selector("img[alt='Cart']").click()
driver.find_element_by_xpath("//button[text()='PROCEED TO CHECKOUT']").click()
wait = WebDriverWait(driver, 8)
wait.until(expected_conditions.presence_of_element_located((By.CLASS_NAME, "promoCode")))
veggies = driver.find_elements_by_css_selector("p.product-name")

for veg in veggies:
    list2.append(veg.text)
print(list2)
originalAmount = driver.find_element_by_css_selector(".discountAmt").text
driver.find_element_by_class_name("PromoCode").send_keys("rahulshettyacademy")
driver.find_element_by_css_selector(".promoBtn").click()
wait.until(expected_conditions.presence_of_element_located((By.CSS_SELECTOR,"span.promoInfo")))
discountAmount = driver.find_element_by_css_selector(".discountAmt").text
assert float(discountAmount) < int(originalAmount)
print(driver.find_element_by_css_selector("span.promoInfo").text)
amounts = driver.find_elements_by_xpath("//tr/td[5]/p")
sum = 0
for amount in amounts:
    sum = sum + int(amount.text)
print(sum)
totalAmount = int(driver.find_element_by_class_name("totAmt").text)
assert sum == totalAmount

for num in range(1,101):
if num %3 == 0 and num %5 == 0:
print("FizzBuzz")
elif num %3 == 0:
print("Fizz")
elif num %5 ==0:
print("Buzz")
else:
print(num)
