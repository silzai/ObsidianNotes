```python
from selenium import webdriver

from selenium.webdriver.common.by import By

import os

import glob

import argparse

  

# setting up argparse

parser = argparse.ArgumentParser(description ="Getting faculty number from command line")

parser.add_argument("faculty_number")

args = parser.parse_args()

  

# setting up selenium

service = webdriver.ChromeService(executable_path="/usr/bin/chromedriver/chromedriver")

driver = webdriver.Chrome(service=service)

  

def get_page_source(driver, faculty_counter: int, page_counter: int) -> str:

"""

template string for asu.edu to replace faculty number and page number

"""

url_template = "https://www.asu.edu.eg/staffPortal/en/profileSearch?faculty={faculty}&page={page}"

url = url_template.format(faculty=faculty_counter, page=page_counter)

driver.get(url)

return driver.page_source

  

def check_if_no_more_pages(driver) -> bool:

"""

checking by XPATH of "No Results Were Found" element

"""

try:

driver.find_element(By.TAG_NAME, "table")

return False

except:

return True

  

def get_latest_page_faculty():

"""

code to resume execution from last saved source file

"""

try:

faculty_counter = args.faculty_number

all_dirs = glob.glob(f"./faculties/{faculty_counter}/**", recursive=True)

files = [f for f in all_dirs if os.path.isfile(f)]

latest_file = max(files, key=os.path.getctime)

file_name_split = latest_file.split("/")

page_counter = int(file_name_split[3])

# adding 1 so that we continue further from where we left off

page_counter += 1

except:

page_counter = 1

return page_counter, faculty_counter

  

def main():

# loop to go through all faculties and pages

next_page = ""

  

page_counter, faculty_counter = get_latest_page_faculty()

page_counter = 27

  

try:

os.mkdir(f"./faculties/{faculty_counter}")

except:

pass

# page loop

while(True):

next_page = get_page_source(driver, faculty_counter=faculty_counter, page_counter=page_counter)

# break if reached end of pages

if (check_if_no_more_pages(driver=driver)):

break

pageFile = open(f"./faculties/{faculty_counter}/{page_counter}", 'w')

pageFile.write(f"{next_page}")

pageFile.close()

page_counter += 1

  

driver.close()

  

if __name__ == "__main__":

main()
```