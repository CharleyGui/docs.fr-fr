---
title: 'Procédure : améliorer le délai de démarrage des applications clientes WCF à l’aide de XmlSerializer'
ms.date: 03/30/2017
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
ms.openlocfilehash: b163f4478794797ea910e39ba2368c602218f13b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586100"
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a>Procédure : améliorer le délai de démarrage des applications clientes WCF à l’aide de XmlSerializer
Les applications clientes et de services qui utilisent des types de données sérialisables à l'aide de <xref:System.Xml.Serialization.XmlSerializer> génèrent et compilent le code de sérialisation de ces types de données lors de l'exécution, ce qui peut provoquer des performances de démarrage lentes.  
  
> [!NOTE]
>  Le code de sérialisation prégénéré est réservé aux applications clientes, pas aux services.  
  
 Le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) peut améliorer les performances de démarrage de ces applications en générant le code de sérialisation nécessaires à partir des assemblys compilés pour l’application. Svcutil.exe génère le code de sérialisation de tous les types de données utilisés dans les contrats de service de l'assembly d'application compilé qui peut être sérialisé à l'aide de <xref:System.Xml.Serialization.XmlSerializer>. Les contrats de service et d'opération qui utilisent <xref:System.Xml.Serialization.XmlSerializer> sont marqués avec <xref:System.ServiceModel.XmlSerializerFormatAttribute>.  
  
### <a name="to-generate-xmlserializer-serialization-code"></a>Pour générer du code de sérialisation XmlSerializer.  
  
1. Compilez votre code de service ou client dans un ou plusieurs assemblys.  
  
2. Ouvrez une invite de commandes du Kit de développement SDK.  
  
3. À l'invite de commandes, lancez l'outil Svcutil.exe à l'aide du format suivant.  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     L'argument `assemblyPath` spécifie le chemin d'accès à un assembly contenant des types de contrat de service. Svcutil.exe génère le code de sérialisation de tous les types de données utilisés dans les contrats de service de l'assembly d'application compilé qui peut être sérialisé à l'aide de <xref:System.Xml.Serialization.XmlSerializer>.  
  
     Svcutil.exe peut uniquement générer du code de sérialisation C#. Un fichier de code source est généré pour chaque assembly d'entrée. Vous ne pouvez pas utiliser le **/language** commutateur pour modifier le langage du code généré.  
  
     Pour spécifier le chemin d’accès aux assemblys dépendants, utilisez le **/reference** option.  
  
4. Rendez le code de sérialisation généré disponible pour votre application en utilisant l'une des options suivantes :  
  
    1. Compilez le code de sérialisation généré dans un assembly séparé portant le nom [*assembly d’origine*]. XmlSerializers.dll (par exemple, MyApp.XmlSerializers.dll). Votre application doit être en mesure de charger l'assembly, qui doit être signé avec la même clé que l'assembly d'origine. Si vous recompilez l'assembly d'origine, vous devez régénérer l'assembly de sérialisation.  
  
    2. Compilez le code de sérialisation généré dans un assembly distinct et utilisez <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> sur le contrat de service qui utilise <xref:System.ServiceModel.XmlSerializerFormatAttribute>. Définissez les propriétés <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> ou <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> pour pointer vers l'assembly de sérialisation compilé.  
  
    3. Compilez le code de sérialisation généré dans votre assembly d'application et ajoutez <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> au contrat de service qui utilise <xref:System.ServiceModel.XmlSerializerFormatAttribute>. Ne définissez pas les propriétés <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> ou <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A>. L'assembly de sérialisation par défaut est supposé être l'assembly actuel.  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a>Pour générer le code de sérialisation XmlSerializer dans Visual Studio  
  
1. Créer le service WCF et le client projets dans Visual Studio. Ensuite, ajoutez une référence de service au projet client.  
  
2. Ajouter un <xref:System.ServiceModel.XmlSerializerFormatAttribute> au contrat de service dans le *reference.cs* fichier dans le projet d’application cliente sous **serviceReference** -> **reference.svcmap** . Notez que vous devez afficher tous les fichiers dans **l’Explorateur de solutions** pour afficher ces fichiers.  
  
3. Générez l’application client.  
  
4. Utilisez le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pour créer un sérialiseur prégénéré *.cs* fichier à l’aide de la commande :  
  
    ```  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     L’argument assemblyPath Spécifie le chemin d’accès à l’assembly de client WCF.  
  
     Par exemple :  
  
    ```  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     Le *WCFClient.XmlSerializers.dll.cs* fichier sera généré.  
  
5. Compilez l’assembly de sérialisation prégénéré.  
  
     Selon l’exemple à l’étape précédente, la commande de compilation serait le suivant :  
  
    ```  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     Assurez-vous que le texte généré *WCFClient.XmlSerializers.dll* est dans le même répertoire que l’application cliente, c'est-à-dire *WCFClient.exe* dans ce cas.  
  
6. Exécutez l’application cliente comme d’habitude. L’assembly de sérialisation prégénéré servira.  
  
## <a name="example"></a>Exemple  
 La commande suivante génère des types de sérialisation pour les types `XmlSerializer` que les contrats de service de l'assembly utilisent.  
  
```  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a>Voir aussi

- [Outil ServiceModel Metadata Utility (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
