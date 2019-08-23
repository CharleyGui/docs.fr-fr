---
title: 'Procédure : utiliser Svcutil.exe pour exporter des métadonnées de code de service compilé'
ms.date: 03/30/2017
ms.assetid: 95d0aed3-16a2-4398-89bb-39418eeb7355
ms.openlocfilehash: b8ddbaf896ee4c6ea8b6f8e8ce7d0ecef28140ea
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932574"
---
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a><span data-ttu-id="bf1ea-102">Procédure : utiliser Svcutil.exe pour exporter des métadonnées de code de service compilé</span><span class="sxs-lookup"><span data-stu-id="bf1ea-102">How to: Use Svcutil.exe to Export Metadata from Compiled Service Code</span></span>
<span data-ttu-id="bf1ea-103">Svcutil.exe peut exporter les métadonnées pour des services, des contrats et des types de données dans des assemblys compilés, comme suit :</span><span class="sxs-lookup"><span data-stu-id="bf1ea-103">Svcutil.exe can export metadata for services, contracts, and data types in compiled assemblies, as follows:</span></span>  
  
- <span data-ttu-id="bf1ea-104">Pour exporter les métadonnées pour tous les contrats de service compilés pour un ensemble d'assemblys en utilisant Svcutil.exe, spécifiez les assemblys en tant que paramètres d'entrée.</span><span class="sxs-lookup"><span data-stu-id="bf1ea-104">To export metadata for all compiled service contracts for a set of assemblies using Svcutil.exe, specify the assemblies as input parameters.</span></span> <span data-ttu-id="bf1ea-105">Il s’agit du comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="bf1ea-105">This is the default behavior.</span></span>  
  
- <span data-ttu-id="bf1ea-106">Pour exporter les métadonnées pour un service compilé en utilisant Svcutil.exe, spécifiez le ou les assemblys de service en tant que paramètres d'entrée.</span><span class="sxs-lookup"><span data-stu-id="bf1ea-106">To export metadata for a compiled service using Svcutil.exe, specify the service assembly or assemblies as input parameters.</span></span> <span data-ttu-id="bf1ea-107">Vous devez utiliser l'option `/serviceName` pour indiquer le nom de configuration du service que vous souhaitez exporter.</span><span class="sxs-lookup"><span data-stu-id="bf1ea-107">You must use the `/serviceName` option to indicate the configuration name of the service you want to export.</span></span> <span data-ttu-id="bf1ea-108">Svcutil.exe charge automatiquement le fichier de configuration pour l'assembly exécutable spécifié.</span><span class="sxs-lookup"><span data-stu-id="bf1ea-108">Svcutil.exe automatically loads the configuration file for the specified executable assembly.</span></span>  
  
- <span data-ttu-id="bf1ea-109">Pour exporter tous les types de contrats de données dans un ensemble d'assemblys, utilisez l'option `/dataContractOnly`.</span><span class="sxs-lookup"><span data-stu-id="bf1ea-109">To export all data contract types within a set of assemblies, use the `/dataContractOnly` option.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf1ea-110">Utilisez l’option `/reference` pour spécifier les chemins d’accès à tous les assemblys dépendants.</span><span class="sxs-lookup"><span data-stu-id="bf1ea-110">Use the `/reference` option to specify the file paths to any dependent assemblies.</span></span>  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a><span data-ttu-id="bf1ea-111">Pour exporter les métadonnées pour des contrats de service compilés</span><span class="sxs-lookup"><span data-stu-id="bf1ea-111">To export metadata for compiled service contracts</span></span>  
  
1. <span data-ttu-id="bf1ea-112">Compilez les implémentations de vos contrats de service dans une ou plusieurs bibliothèques de classes.1</span><span class="sxs-lookup"><span data-stu-id="bf1ea-112">Compile your service contract implementations into one or more class libraries.1</span></span>  
  
2. <span data-ttu-id="bf1ea-113">Exécutez Svcutil.exe sur les assemblys compilés.</span><span class="sxs-lookup"><span data-stu-id="bf1ea-113">Run Svcutil.exe on the compiled assemblies.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="bf1ea-114">Vous pouvez être amené à utiliser le commutateur `/reference` pour spécifier le chemin d’accès à tous les assemblys dépendants.</span><span class="sxs-lookup"><span data-stu-id="bf1ea-114">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```  
    svcutil.exe Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-a-compiled-service"></a><span data-ttu-id="bf1ea-115">Pour exporter les métadonnées pour un service compilé</span><span class="sxs-lookup"><span data-stu-id="bf1ea-115">To export metadata for a compiled service</span></span>  
  
1. <span data-ttu-id="bf1ea-116">Compilez votre implémentation de service dans un assembly exécutable.</span><span class="sxs-lookup"><span data-stu-id="bf1ea-116">Compile your service implementation into an executable assembly.</span></span>  
  
2. <span data-ttu-id="bf1ea-117">Créez un fichier de configuration pour l'exécutable de votre service et ajoutez une configuration de service.</span><span class="sxs-lookup"><span data-stu-id="bf1ea-117">Create a configuration file for your service executable and add a service configuration.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="MyService" >  
            <endpoint address="finder" contract="IPeopleFinder" binding="wsHttpBinding" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
3. <span data-ttu-id="bf1ea-118">Exécutez Svcutil.exe sur l'exécutable du service compilé en utilisant le commutateur `/serviceName` pour spécifier le nom de configuration du service.</span><span class="sxs-lookup"><span data-stu-id="bf1ea-118">Run Svcutil.exe on the compiled service executable using the `/serviceName` switch to specify the configuration name of the service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="bf1ea-119">Vous pouvez être amené à utiliser le commutateur `/reference` pour spécifier le chemin d’accès à tous les assemblys dépendants.</span><span class="sxs-lookup"><span data-stu-id="bf1ea-119">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a><span data-ttu-id="bf1ea-120">Pour exporter les métadonnées pour des contrats de données compilés</span><span class="sxs-lookup"><span data-stu-id="bf1ea-120">To export metadata for compiled data contracts</span></span>  
  
1. <span data-ttu-id="bf1ea-121">Compilez les implémentations de vos contrats de données dans une ou plusieurs bibliothèques de classes.</span><span class="sxs-lookup"><span data-stu-id="bf1ea-121">Compile your data contract implementations into one or more class libraries.</span></span>  
  
2. <span data-ttu-id="bf1ea-122">Exécutez Svcutil.exe sur les assemblys compilés en utilisant le commutateur `/dataContract` pour spécifier que seules les métadonnées pour les contrats de données doivent être générées.</span><span class="sxs-lookup"><span data-stu-id="bf1ea-122">Run Svcutil.exe on the compiled assemblies using the `/dataContract` switch to specify that only metadata for data contracts should be generated.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="bf1ea-123">Vous pouvez être amené à utiliser le commutateur `/reference` pour spécifier le chemin d’accès à tous les assemblys dépendants.</span><span class="sxs-lookup"><span data-stu-id="bf1ea-123">You might need to use the `/reference` switch to specify the file path to any dependent assemblies.</span></span>  
  
    ```  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a><span data-ttu-id="bf1ea-124">Exemples</span><span class="sxs-lookup"><span data-stu-id="bf1ea-124">Example</span></span>  
 <span data-ttu-id="bf1ea-125">L'exemple ci-dessous montre comment générer les métadonnées pour l'implémentation et la configuration d'un service simple.</span><span class="sxs-lookup"><span data-stu-id="bf1ea-125">The following example demonstrates how to generate metadata for a simple service implementation and configuration.</span></span>  
  
 <span data-ttu-id="bf1ea-126">Pour exporter les métadonnées pour le contrat de service :</span><span class="sxs-lookup"><span data-stu-id="bf1ea-126">To export metadata for the service contract.</span></span>  
  
```  
svcutil.exe Contracts.dll  
```  
  
 <span data-ttu-id="bf1ea-127">Pour exporter les métadonnées pour les contrats de données :</span><span class="sxs-lookup"><span data-stu-id="bf1ea-127">To export metadata for the data contracts.</span></span>  
  
```  
svcutil.exe /dataContractOnly Contracts.dll  
```  
  
 <span data-ttu-id="bf1ea-128">Pour exporter les métadonnées pour l'implémentation de service :</span><span class="sxs-lookup"><span data-stu-id="bf1ea-128">To export metadata for the service implementation.</span></span>  
  
```  
svcutil.exe /serviceName:MyService Service.exe /reference:<path>/Contracts.dll  
```  
  
 <span data-ttu-id="bf1ea-129">`<path>` est le chemin d'accès à Contracts.dll.</span><span class="sxs-lookup"><span data-stu-id="bf1ea-129">The `<path>` is the path to Contracts.dll.</span></span>  
  
```  
// The following service contract and data contracts are compiled into   
// Contracts.dll.  
[ServiceContract(ConfigurationName="IPeopleFinder")]  
public interface IPersonFinder  
{  
    [OperationContract]  
    Address GetAddress(Person s);  
}  
  
[DataContract]  
public class Person  
{  
    [DataMember]  
    public string firstName;  
    [DataMember]  
    public string lastName;  
    [DataMember]  
    public int age;  
}  
  
[DataContract]  
public class Address  
{  
    [DataMember]  
    public string city;  
    [DataMember]  
    public string state;  
    [DataMember]  
    public string street;  
    [DataMember]  
    public int zipCode;  
    [DataMember]  
    public Person person;  
}  
  
// The following service implementation is compiled into Service.exe.     
// This service uses the contracts specified in Contracts.dll.  
[ServiceBehavior(ConfigurationName = "MyService")]  
public class MyService : IPersonFinder  
{  
    public Address GetAddress(Person person)  
    {  
        Address address = new Address();  
        address.person = person;  
        return address;  
    }  
}  
  
<!-- The following is the configuration file for Service.exe. -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="MyService">  
         <endpoint  address="finder"  
                    binding="basicHttpBinding"  
                    contract="IPeopleFinder"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf1ea-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf1ea-130">See also</span></span>

- [<span data-ttu-id="bf1ea-131">Outil ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="bf1ea-131">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="bf1ea-132">Exportation et importation de métadonnées</span><span class="sxs-lookup"><span data-stu-id="bf1ea-132">Exporting and Importing Metadata</span></span>](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
