```python
from selenium import webdriver

import os

import glob

  

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

  

def get_latest_page_faculty():

"""

code to resume execution from last saved source file

"""

try:

all_dirs = glob.glob("./faculties/**", recursive=True)

files = [f for f in all_dirs if os.path.isfile(f)]

latest_file = max(files, key=os.path.getctime)

file_name_split = latest_file.split("/")

faculty_counter = int(file_name_split[2])

page_counter = int(file_name_split[3])

# adding 1 so that we continue further from where we left off

page_counter += 1

except:

page_counter = 1

faculty_counter = 1

return page_counter, faculty_counter

  

def main():

# loop to go through all faculties and pages

next_page = ""

  

page_counter, faculty_counter = get_latest_page_faculty()

  

# faculty loop

while (True):

try:

os.mkdir(f"./faculties/{faculty_counter}")

except:

pass

# page loop

while(True):

  

next_page = get_page_source(driver, faculty_counter=faculty_counter, page_counter=page_counter)

# break if reached end of pages

if (next_page.__contains__("No Results Were Found")):

break

pageFile = open(f"./faculties/{faculty_counter}/{page_counter}", 'w')

pageFile.write(f"{next_page}")

pageFile.close()

page_counter += 1

  

page_counter = 1 # re-initializing the page counter

faculty_counter += 1

next_page = get_page_source(driver, faculty_counter=faculty_counter, page_counter=page_counter)

# break if reached end of pages

if (next_page.__contains__("No Results Were Found")):

break

  

driver.close()

  

if __name__ == "__main__":

main()
```