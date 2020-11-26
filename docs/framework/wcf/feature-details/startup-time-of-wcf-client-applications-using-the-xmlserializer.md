---
title: 'Procédure : améliorer le délai de démarrage des applications clientes WCF à l’aide de XmlSerializer'
ms.date: 03/30/2017
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
ms.openlocfilehash: ac54a766161db146331a3e072b97822b609344c0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96246379"
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a>Procédure : améliorer le délai de démarrage des applications clientes WCF à l’aide de XmlSerializer

Les applications clientes et de services qui utilisent des types de données sérialisables à l'aide de <xref:System.Xml.Serialization.XmlSerializer> génèrent et compilent le code de sérialisation de ces types de données lors de l'exécution, ce qui peut provoquer des performances de démarrage lentes.  
  
> [!NOTE]
> Le code de sérialisation prégénéré est réservé aux applications clientes, pas aux services.  
  
 L' [outil ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) peut améliorer les performances de démarrage de ces applications en générant le code de sérialisation nécessaire à partir des assemblys compilés pour l’application. Svcutil.exe génère le code de sérialisation de tous les types de données utilisés dans les contrats de service de l'assembly d'application compilé qui peut être sérialisé à l'aide de <xref:System.Xml.Serialization.XmlSerializer>. Les contrats de service et d'opération qui utilisent <xref:System.Xml.Serialization.XmlSerializer> sont marqués avec <xref:System.ServiceModel.XmlSerializerFormatAttribute>.  
  
### <a name="to-generate-xmlserializer-serialization-code"></a>Pour générer du code de sérialisation XmlSerializer.  
  
1. Compilez votre code de service ou client dans un ou plusieurs assemblys.  
  
2. Ouvrez une invite de commandes du Kit de développement SDK.  
  
3. À l'invite de commandes, lancez l'outil Svcutil.exe à l'aide du format suivant.  
  
    ```console  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     L'argument `assemblyPath` spécifie le chemin d'accès à un assembly contenant des types de contrat de service. Svcutil.exe génère le code de sérialisation de tous les types de données utilisés dans les contrats de service de l'assembly d'application compilé qui peut être sérialisé à l'aide de <xref:System.Xml.Serialization.XmlSerializer>.  
  
     Svcutil.exe peut uniquement générer du code de sérialisation C#. Un fichier de code source est généré pour chaque assembly d'entrée. Vous ne pouvez pas utiliser le commutateur **/Language** pour modifier la langue du code généré.  
  
     Pour spécifier le chemin d’accès aux assemblys dépendants, utilisez l’option **/Reference** .  
  
4. Rendez le code de sérialisation généré disponible pour votre application en utilisant l'une des options suivantes :  
  
    1. Compilez le code de sérialisation généré dans un assembly séparé portant le nom [*assembly d’origine*] .XmlSerializers.dll (par exemple, MyApp.XmlSerializers.dll). Votre application doit être en mesure de charger l'assembly, qui doit être signé avec la même clé que l'assembly d'origine. Si vous recompilez l'assembly d'origine, vous devez régénérer l'assembly de sérialisation.  
  
    2. Compilez le code de sérialisation généré dans un assembly distinct et utilisez <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> sur le contrat de service qui utilise <xref:System.ServiceModel.XmlSerializerFormatAttribute>. Définissez les propriétés <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> ou <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> pour pointer vers l'assembly de sérialisation compilé.  
  
    3. Compilez le code de sérialisation généré dans votre assembly d'application et ajoutez <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> au contrat de service qui utilise <xref:System.ServiceModel.XmlSerializerFormatAttribute>. Ne définissez pas les propriétés <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> ou <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A>. L'assembly de sérialisation par défaut est supposé être l'assembly actuel.  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a>Pour générer le code de sérialisation XmlSerializer dans Visual Studio  
  
1. Créez le service WCF et les projets clients dans Visual Studio. Ensuite, ajoutez une référence de service au projet client.  
  
2. Ajoutez un <xref:System.ServiceModel.XmlSerializerFormatAttribute> au contrat de service dans le fichier *Reference.cs* dans le projet d’application cliente sous **serviceReference**  ->  **Reference. svcmap**. Notez que vous devez afficher tous les fichiers dans **Explorateur de solutions** pour voir ces fichiers.  
  
3. Générez l’application cliente.  
  
4. Utilisez l' [outil ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) pour créer un fichier serializer *. cs* pré-généré à l’aide de la commande :  
  
    ```console  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     L’argument assemblyPath spécifie le chemin d’accès à l’assembly du client WCF.  
  
     Par exemple :  
  
    ```console  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     Le fichier *WCFClient.XmlSerializers.dll. cs* sera généré.  
  
5. Compilez l’assembly de sérialisation préalablement généré.  
  
     En fonction de l’exemple de l’étape précédente, la commande compile est la suivante :  
  
    ```console  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     Assurez-vous que le *WCFClient.XmlSerializers.dll* généré se trouve dans le même répertoire que l’application cliente, qui est *WCFClient.exe* dans ce cas.  
  
6. Exécutez l’application cliente comme d’habitude. L’assembly de sérialisation prégénéré sera utilisé.  
  
## <a name="example"></a> Exemple  

 La commande suivante génère des types de sérialisation pour les types `XmlSerializer` que les contrats de service de l'assembly utilisent.  
  
```console  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a>Voir aussi

- [Outil Service Model Metadata Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)
