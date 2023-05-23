# Azure-ML
Implementation & Deployment of ML Services in Azure

<img width="354" alt="image" src="https://user-images.githubusercontent.com/72096831/211571279-39b910df-2cb1-465f-9ada-3eb04b1a9982.png">


    datastore = Datastore.get(ws, datastore_name='salarydata')
    datastore.upload_files(files=['./model/training.py'],
               target_path="/anomaly")
               
---
    
    # delete folder inside default datastore
    from azureml.core import Workspace
    from azure.storage.blob import BlobServiceClient

    # Connect to your Azure Machine Learning workspace
    workspace = Workspace.from_config()

    # Get the default datastore
    default_datastore = workspace.get_default_datastore()

    # Get the container name and the folder path you want to delete
    container_name = default_datastore.container_name
    folder_path = "datadrift-data"

    # Retrieve the connection string for the default datastore
    connection_string = ''

    # Create a BlobServiceClient using the connection string
    blob_service_client = BlobServiceClient.from_connection_string(connection_string)

    # Get a reference to the container
    container_client = blob_service_client.get_container_client(container_name)

    # List the blobs in the container with the specified folder path
    blobs = container_client.list_blobs(name_starts_with=folder_path)

    # Delete the blobs belonging to the folder
    for blob in blobs:
        container_client.delete_blob(blob.name)

    print("Folder deleted successfully.")


    
