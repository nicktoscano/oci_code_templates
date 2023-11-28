# oci_code_templates

## How to Set Up a New Data Science Notebook:

Before using a new data science notebook, you need to perform a few setup procedures.

1. Create a notebook config file

### Create a Config File:
* Open a new terminal in Oracle Data Science notebook session
  
* Create a folder named .oci under the /home/datascience
  ```
  $ mkdir ~/.oci
  $ cd .oci
  $ vi config
  ```

* Paste the config file contents and exit vi.
  * To paste in vi first enter insert mode by pushing 'i'.
  * To exit vi hit esc. Then hit 'w' and 'q'. Press Enter.

## Example Config File:
The format for the config file should be as follows:

#### Format:
[DEFAULT] <br/>
user=user-ocid <br/>
fingerprint=fingerprint <br/>
tenancy=tenancy-ocid <br/>
region=your-service-oci-region <br/>
key_file=path-to-your-private-keyfile

#### Example:
[DEFAULT] <br/>
user=ocid9.user.oc9..zzzzzzzzzzzjzjzjzhjkzgzjhglgzliuogyoyaglifueqwfhrkjq <br/>
fingerprint=12:45:23:w8:34:67:4d:94:71:43:11:4r:g1:82:4t:5y <br/>
tenancy=ocid9.tenancy.oc9..akqjawesfbdnalkjdfhalsiuheraahkjaksdjhfliaueha <br/>
region=us-ashburn-1 <br/>
key_file=~/.ssh/your-file.pem  


Note: If you have not already added an API key to your cloud profile, you will need to complete this step first. 
You can create create a pem file manually using the terminal in Data Science (see steps below), or you can 
create the file under your user profile in the cloud console. Go to Identity/Users/User Details/API Keys.

## Manually Create .pem file:

* Generate an API signing Key
  ```
  $ openssl genrsa -out ~/.oci/oci_api_key.pem -aes128 2048
  ```

* Generate the public key
  ```
  $ openssl rsa -pubout -in ~/.oci/oci_api_key.pem -out ~/.oci/oci_api_key_public.pem
  ```

* Generate is the key's fingerprint
  ```
  $ openssl rsa -pubout -outform DER -in ~/.oci/oci_api_key.pem | openssl md5 -c
  ```

* I recommend downloading the keys and storing them for later use. You will need to load them into the user cloud console.
  Also, you can reuse these keys in other notebooks.

* In cloud console go to User/User Details/API Keys.

* Select Add API Key and select 'choose public key file'.

* Upload the public key file. You can also choose to paste the public key file if you copied it.
  You can copy the public key int he terminal using:
  ```
  $ $ pbcopy < ~/.ssh/keyname.pub
  ```

* Once created, view the details of the key file. You can copy all the infomration required for the config file from here.

* Next, go back to your data science notebook in the Oracle Cloud Data Science Service.

