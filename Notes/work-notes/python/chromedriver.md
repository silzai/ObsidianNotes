```python
def setup_chromedriver():
# setting up selenium
	options = webdriver.ChromeOptions()
	options.add_argument("--no-sandbox")
	options.add_argument("--disable-dev-shm-usage")
	options.add_argument('--ignore-certificate-errors')
	#options.add_argument("--test-type")
	options.add_argument("--headless")
	options.add_argument("--incognito")
	options.add_argument('--disable-gpu') if os.name == 'nt' else None # Windows workaround
	options.add_argument("--verbose")
	options.add_argument('--disable-notifications')
	options.add_argument('--lang=en-GB')
	options.add_experimental_option('prefs', {'intl.accept_languages': 'en,en_US'})
	
	return webdriver.Chrome(options = options)
```