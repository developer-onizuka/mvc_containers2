# mvc_containers2

# 1. Install dotnet-sdk
https://docs.microsoft.com/ja-jp/dotnet/core/install/linux-ubuntu#2104-
```
wget https://packages.microsoft.com/config/ubuntu/21.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
rm packages-microsoft-prod.deb

sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-5.0
  
git clone https://github.com/developer-onizuka/mvc_containers2.git
cd mvc_containers2/Employee
dotnet add package MongoDB.Driver
sudo docker run -d --rm --name mongo -p 27017:27017 mongo:latest

export MONGO="localhost:27017"
dotnet run
dotnet publish -c release -r linux-x64 --self-contained
```



