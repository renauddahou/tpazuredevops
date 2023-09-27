#### Connexion à AZURE 

``url: https://portal.azure.com/``

``Email: training-user-15@soatformation.onmicrosoft.com``

``Password: 17@17lenaic``

#### Installation du module AZ et Authentification dans powershell 


``Get-Module -ListAvailable Az``

``Install-Module -Name Az -AllowClobber -Force -Confirm:$false``


``Update-Module -Name Az``


``Import-Module Az``



``Connect-AzAccount -UseDeviceAuthentication``


#### Notre premiere commande pour voir les regions ou sont disponible le service vitualMachines

``
$resources = Get-AzResourceProvider -ProviderNamespace Microsoft.Compute
$resources.ResourceTypes.Where({$_.ResourceTypeName -eq 'virtualMachines'}).Locations
``
