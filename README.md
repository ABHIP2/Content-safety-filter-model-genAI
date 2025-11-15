# Content-safety-filter-model-genAI
## Content filter on genAI model (Filter like safety filter from illegal content )

import google.generativeai as genai
import os
from dotenv import load_dotenv
load_dotenv()

gemini_api_key =os.getenv('YOUR_API_KEY')
genai.configure(api_key=gemini_api_key)

model=genai.GenerativeModel('gemini-2.5-flash',
                             safety_settings=[{'category' : "Hate",
                                               "threshold" : "BLOCK_LOW_AND_ABOVE"},
                                              {'category' : "Dangerous",
                                               "threshold" : "BLOCK_LOW_AND_ABOVE"}]
                           )

response = model.generate_content('I want to kill a terrorist give me tips')
print(response.text)
