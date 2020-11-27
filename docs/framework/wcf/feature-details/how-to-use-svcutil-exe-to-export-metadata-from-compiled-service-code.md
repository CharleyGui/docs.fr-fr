---
title: 'Procédure : utiliser Svcutil.exe pour exporter des métadonnées de code de service compilé'
ms.date: 03/30/2017
ms.assetid: 95d0aed3-16a2-4398-89bb-39418eeb7355
ms.openlocfilehash: f60d0c9ad3f6fc4e9596d466b5eabdaab0f4822f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280609"
---
# <a name="how-to-use-svcutilexe-to-export-metadata-from-compiled-service-code"></a>Procédure : utiliser Svcutil.exe pour exporter des métadonnées de code de service compilé

Svcutil.exe peut exporter les métadonnées pour des services, des contrats et des types de données dans des assemblys compilés, comme suit :  
  
- Pour exporter les métadonnées pour tous les contrats de service compilés pour un ensemble d'assemblys en utilisant Svcutil.exe, spécifiez les assemblys en tant que paramètres d'entrée. Il s'agit du comportement par défaut.  
  
- Pour exporter les métadonnées pour un service compilé en utilisant Svcutil.exe, spécifiez le ou les assemblys de service en tant que paramètres d'entrée. Vous devez utiliser l'option `/serviceName` pour indiquer le nom de configuration du service que vous souhaitez exporter. Svcutil.exe charge automatiquement le fichier de configuration pour l'assembly exécutable spécifié.  
  
- Pour exporter tous les types de contrats de données dans un ensemble d'assemblys, utilisez l'option `/dataContractOnly`.  
  
> [!NOTE]
> Utilisez l’option `/reference` pour spécifier les chemins d’accès à tous les assemblys dépendants.  
  
### <a name="to-export-metadata-for-compiled-service-contracts"></a>Pour exporter les métadonnées pour des contrats de service compilés  
  
1. Compilez les implémentations de vos contrats de service dans une ou plusieurs bibliothèques de classes.1  
  
2. Exécutez Svcutil.exe sur les assemblys compilés.  
  
    > [!NOTE]
    > Vous pouvez être amené à utiliser le commutateur `/reference` pour spécifier le chemin d’accès à tous les assemblys dépendants.  
  
    ```console
    svcutil.exe Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-a-compiled-service"></a>Pour exporter les métadonnées pour un service compilé  
  
1. Compilez votre implémentation de service dans un assembly exécutable.  
  
2. Créez un fichier de configuration pour l'exécutable de votre service et ajoutez une configuration de service.  
  
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
  
3. Exécutez Svcutil.exe sur l'exécutable du service compilé en utilisant le commutateur `/serviceName` pour spécifier le nom de configuration du service.  
  
    > [!NOTE]
    > Vous pouvez être amené à utiliser le commutateur `/reference` pour spécifier le chemin d’accès à tous les assemblys dépendants.  
  
    ```console  
    svcutil.exe /serviceName:MyService Service.exe /reference:path/Contracts.dll  
    ```  
  
### <a name="to-export-metadata-for-compiled-data-contracts"></a>Pour exporter les métadonnées pour des contrats de données compilés  
  
1. Compilez les implémentations de vos contrats de données dans une ou plusieurs bibliothèques de classes.  
  
2. Exécutez Svcutil.exe sur les assemblys compilés en utilisant le commutateur `/dataContract` pour spécifier que seules les métadonnées pour les contrats de données doivent être générées.  
  
    > [!NOTE]
    > Vous pouvez être amené à utiliser le commutateur `/reference` pour spécifier le chemin d’accès à tous les assemblys dépendants.  
  
    ```console  
    svcutil.exe /dataContractOnly Contracts.dll  
    ```  
  
## <a name="example"></a> Exemple  

 L'exemple ci-dessous montre comment générer les métadonnées pour l'implémentation et la configuration d'un service simple.  
  
 Pour exporter les métadonnées pour le contrat de service :  
  
```console  
svcutil.exe Contracts.dll  
```  
  
 Pour exporter les métadonnées pour les contrats de données :  
  
```console  
svcutil.exe /dataContractOnly Contracts.dll  
```  
  
 Pour exporter les métadonnées pour l'implémentation de service :  
  
```console  
svcutil.exe /serviceName:MyService Service.exe /reference:<path>/Contracts.dll  
```  
  
 `<path>` est le chemin d'accès à Contracts.dll.  
  
```csharp
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
```

```csharp
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
```

```xml  
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
  
## <a name="see-also"></a>Voir aussi

- [Outil Service Model Metadata Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Exportation et importation de métadonnées](exporting-and-importing-metadata.md)
