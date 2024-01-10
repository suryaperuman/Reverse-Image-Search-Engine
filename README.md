# Simple Image Search Engine


## Overview
- Simple image-based image search engine using Keras + Flask. You can launch the search engine just by running two python scripts. `offline.py`: extracts a deep-feature from each database image. Each feature is a 4096D fc6 activation from a VGG16 model with ImageNet pre-trained weights. `server.py`: This  runs a web-server. You can send your query image to the server via a Flask web-interface. 
- GPUs are not required.

## Usage
```bash
git clone https://github.com/suryaperuman/Reverse-Search-Engine.git
cd sis
pip install -r requirements.txt

# Put your image files (*.jpg) on static/img

# Then fc6 features are extracted and saved on static/feature
# Note that it takes time for the first time because Keras downloads the VGG weights.
python offline.py

# Now you can do the search via localhost:5000
python server.py
```

## Advanced: Launch on AWS
- You can easily launch the search engine server on AWS EC2. Open the port 5000 and launch an EC2 instance. Note that you need to create a security group such that the port 5000 is opened.
- A middle-level CPU instance is sufficient, e.g., m5.large.
- After you log-in to the instance by ssh, please setup the python environment.
- Run `offline.py` and `server.py`. (Advanced) If you'd like to deploy the system in a secure way, please consider running the search engine with the usual web server, e.g., uWSGI + nginx.
- (Advanced) If you want to deploy the system serverlessly, [AWS AppRunner](https://docs.aws.amazon.com/apprunner/latest/dg/what-is-apprunner.html) is the way to go.