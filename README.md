 Docker ile Projeyi Çalıştırmak

Reponun klonlanması:
git clone https://github.com/burakemirhankarakus/ChatBotApi.git ||
cd ChatBotApi  ||

Docker imajının build edilmesi :
docker build -t chatbot-api -f ChatBot.Api/Dockerfile .    ||

API’yi container içinde başlatma :
docker run -d -p 8080:8080 -e ASPNETCORE_ENVIRONMENT=Development chatbot-api ||

https://platform.openai.com/api-keys adresinden api key oluşturup appsettings.json içersine girerek kullanabilirsiniz.
