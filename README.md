# rajesh
pathology tcs
from selenium import webdriver
import time
import unittest

from selenium.webdriver.common.by import By

class LoginTest(unittest.TestCase):

    def setUp(self):
        self.driver = webdriver.Chrome()
        self.driver.get("https://gor-pathology.web.app/")
        self.driver.maximize_window()

    def test_login_with_valid_credentials(self):
        self.driver.find_element(By.NAME,"email").send_keys("test@kennect.io")
        self.driver.find_element(By.NAME,"password").send_keys("Qwerty@1234")
        self.driver.find_element(By.CLASS_NAME,"MuiButton-label").click()
        time.sleep(5)  # Adjust as needed
        self.assertIn("/home", self.driver.current_url)

    def verifying_todo_list(self):
        todo_list = self.driver.find_element(By.XPATH, "//div[text()='TODO']")
        self.assertTrue(todo_list.is_displayed())

    def verifying_test_cost_calculator_tab(self):
        cost_calculator_tab = self.driver.find_element(By.XPATH, "//div[text()='Test Cost Calculator']")
        cost_calculator_tab.click()
        self.driver.find_element(By.ID,"patient-test").click()
        self.driver.find_element(By.XPATH,"//span[text()='Beans - 250₹']").click()
        time.sleep(5)



    def tearDown(self):
        self.driver.quit()

if __name__ == "__main__":
    unittest.main()
