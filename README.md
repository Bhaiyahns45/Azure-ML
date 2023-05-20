# Azure-ML
Implementation & Deployment of ML Services in Azure

<img width="354" alt="image" src="https://user-images.githubusercontent.com/72096831/211571279-39b910df-2cb1-465f-9ada-3eb04b1a9982.png">


    datastore = Datastore.get(ws, datastore_name='salarydata')
    datastore.upload_files(files=['./model/training.py'],
               target_path="/anomaly")

    
