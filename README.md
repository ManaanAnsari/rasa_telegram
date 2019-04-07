# what is this ?
This repo is a result of blog post you can find here <https://medium.com/@manaan1ansari/getting-started-with-rasa-chatbot-and-telegram-part-1-d289977e24ac>
it will help you get up and running with rasa and telegram 

# How To Use ?
first install all the dependencies from requirements.txt 

	pip install -r requirements.txt

	pip install rasa_core_sdk (if needed)

	pip install flask (if needed)

and download spacy english model

	python -m spacy download en


#Train rasa_nlu

	python -m rasa_nlu.train -c nlu/nlu_config.yml --data nlu/nlu_data.md -o models --fixed_model_name nlu --project current --verbose

#Train rasa_core

	python -m rasa_core.train -d core/domain.yml -s core/stories.md -o models/current/dialogue

#start action server

	python -m rasa_core_sdk.endpoint --actions actions

#Run Bot On cmdline

	python3 -m rasa_core.run -d models/current/dialogue -u models/current/nlu --endpoints endpoints.yml

#Run Bot On Telegram
## create bot
create bot using botfather and get the access token

## setup webhook
start tunnel using ngrok or any other services and setup webhook by following url  
https://api.telegram.org/bot'bot token'/setWebhook?url='webhook url'

## chat
enter your bot token in main.py and run main.py
	python3 main.py 
