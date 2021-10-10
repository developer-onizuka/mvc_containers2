# mvc_containers2

# 1. Install dotnet-sdk
See also https://docs.microsoft.com/ja-jp/dotnet/core/install/linux-ubuntu#2104- .
But you might use the Vagrantfile attached in this repository so that you could also install OS itself automatically.
```
$ wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
$ dpkg -i packages-microsoft-prod.deb
$ rm packages-microsoft-prod.deb

$ sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-5.0
```

# 2. git clone this repository and test if it works well
```
$ git clone https://github.com/developer-onizuka/mvc_containers2.git
$ cd mvc_containers2/Employee
$ dotnet add package MongoDB.Driver
$ sudo docker run -d --rm --name mongo -p 27017:27017 mongo:latest
$ export MONGO="localhost:27017"
$ dotnet run
$ curl https://127.0.0.1:5001 -k
```

# 3. (Optional) Compiling
```
$ dotnet publish -c release -r linux-x64 --self-contained
```

# 4. Create Docker container
```
$ sudo docker build -t employee:1.0.0 .
```

# 5. Push it to dockerhub
See https://github.com/developer-onizuka/docker_push .

