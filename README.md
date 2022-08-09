# AES
Automated Essay Scoring System
** Partial was originally from https://github.com/dmmiller612/lecture-summarizer.git **

# Features
 * generate summary on given text
# Main Purpose
deploy the automated essay scoring system on Kubernetes by use Google Cloud Platform.
# Preparing
* Create a new Kubernetes cluster
* Connect to the cluster

# Step 1:
Download the project from gibhub
```
 git clone https://github.com/Quan25/flask-summary.git
```
# Step 2:
* Install ROUGE-1.5.5

* Install libxml-parser-perl
```
  sudo apt-get install libxml-parser-perl
  sudo cpan install XML::Parser::PerlSAX
  sudo cpan install XML::RegExp
  Sudo cpan install XML::DOM
```
* Install pyrouge
```
 git clone https://github.com/bheinzerling/pyrouge.git
 cd pyrouge
 pip install -e .
```
# Step 3:
* Run miniconda installation script 
```
./Miniconda3-latest-Linux-x86_64.sh
```
# step 4:
Create and activate a Python environment 
```
conda create -n myenv python=3.6 
conda activate myenv
pip install -e .
conda install pytorch-cpu==1.1.0 torchvision-cpu==0.3.0 cpuonly -c pytorch
```

# step 5:
Go back to your project folder and download pretrained-bert-model 
```
wget https://s3.amazonaws.com/models.huggingface.co/bert/bert-largeuncased.tar.gz
```
# step 6: 
* Change the path in BertParent.py in summarizer folder 
self.model = BertModel.from_pretrained('YOUR_PROJECT_Directory/bert-largeuncased.tar.gz')
# step 7:
* Install all the following package 
```
pip3 install flask 
pip3 install pandas 
pip3 install sklearn 
pip3 install nltk 
pip3 install gensim==3.8.3 
pip3 install pytorch-pretrained-bert 
pip3 install matplotlib==3.0.0
```

# Step 8:
Run app.py
```
python3 app.py
```

# Step 9:
* Deploy this app on Kubernetes.
* Create a Dockerfile: 
* buliding a docker image.
# step 10:
push this image to the dockerhub.

# step 11:
create aes-deployment.ymal
create aes-service.ymal

# step 12: 
deploy the dockerhub by using minkube.
```
minikube start
minikube addons enable ingress
kubectl apply -f aes-deployment.yaml
kubectl apply -f aes-service.yaml
```
