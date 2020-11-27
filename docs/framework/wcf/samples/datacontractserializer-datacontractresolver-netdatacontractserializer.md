---
title: Utilisation de DataContractSerializer et DataContractResolver pour fournir les fonctionnalités de NetDataContractSerializer
ms.date: 03/30/2017
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
ms.openlocfilehash: 002cd101ddf760e28a71ded0d6a7f4ee29a56c3b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253608"
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a>Utilisation de DataContractSerializer et DataContractResolver pour fournir les fonctionnalités de NetDataContractSerializer

Cet exemple montre comment l'utilisation de <xref:System.Runtime.Serialization.DataContractSerializer> avec un <xref:System.Runtime.Serialization.DataContractResolver> approprié fournit les mêmes fonctionnalités que <xref:System.Runtime.Serialization.NetDataContractSerializer>. Cet exemple montre comment créer le <xref:System.Runtime.Serialization.DataContractResolver> approprié et comment l'ajouter au <xref:System.Runtime.Serialization.DataContractSerializer>.

## <a name="sample-details"></a>Détails de l'exemple

 <xref:System.Runtime.Serialization.NetDataContractSerializer> diffère de <xref:System.Runtime.Serialization.DataContractSerializer> sur un point important : <xref:System.Runtime.Serialization.NetDataContractSerializer> inclut des informations de type CLR dans le XML sérialisé ; <xref:System.Runtime.Serialization.DataContractSerializer> ne le fait pas. Par conséquent, <xref:System.Runtime.Serialization.NetDataContractSerializer> peut être utilisé uniquement si les extrémités de sérialisation et de désérialisation partagent toutes deux les mêmes types CLR. Toutefois, il est recommandé d'utiliser <xref:System.Runtime.Serialization.DataContractSerializer>, car il offre de meilleures performances que <xref:System.Runtime.Serialization.NetDataContractSerializer>. Vous pouvez modifier les informations sérialisées dans <xref:System.Runtime.Serialization.DataContractSerializer> en lui ajoutant un <xref:System.Runtime.Serialization.DataContractResolver>.

 Cet exemple est composé de deux projets. Le premier projet utilise <xref:System.Runtime.Serialization.NetDataContractSerializer> pour sérialiser un objet. Le second projet utilise <xref:System.Runtime.Serialization.DataContractSerializer> avec un <xref:System.Runtime.Serialization.DataContractResolver> pour fournir les mêmes fonctionnalités que le premier projet.

 L'exemple de code suivant illustre l'implémentation d'un <xref:System.Runtime.Serialization.DataContractResolver> personnalisé, nommé `MyDataContractResolver`, qui est ajouté au <xref:System.Runtime.Serialization.DataContractSerializer> du projet DCSwithDCR.

```csharp
class MyDataContractResolver : DataContractResolver
{
    private XmlDictionary dictionary = new XmlDictionary();

    public MyDataContractResolver()
    {
    }

    // Used at deserialization
    // Allows users to map xsi:type name to any Type
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)
    {
        Type type = knownTypeResolver.ResolveName(typeName, typeNamespace, null);
        type ??= Type.GetType(typeName + ", " + typeNamespace);
        return type;
    }

    // Used at serialization
    // Maps any Type to a new xsi:type representation
    public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)
    {
        knownTypeResolver.ResolveType(dataContractType, null, out typeName, out typeNamespace);
        if (typeName == null || typeNamespace == null)
        {
            XmlDictionary dictionary = new XmlDictionary();
            typeName = dictionary.Add(dataContractType.FullName);
            typeNamespace = dictionary.Add(dataContractType.Assembly.FullName);
        }
    }
}
```

#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple

1. À l’aide de Visual Studio 2012, ouvrez le fichier solution DCRSample. sln.

2. Cliquez avec le bouton droit sur le fichier solution et choisissez **Propriétés**.

3. Dans la boîte de dialogue **pages de propriétés** de la solution, sous **Propriétés communes**, **projet de démarrage**, sélectionnez **plusieurs projets de démarrage :**.

4. En regard du projet **DCSwithDCR** , sélectionnez **Démarrer** dans la liste déroulante **action** .

5. En regard du projet **NetDCS** , sélectionnez **Démarrer** dans la liste déroulante **action** .

6. Cliquez sur **OK** pour fermer la boîte de dialogue.

7. Pour générer la solution, appuyez sur Ctrl+Maj+B.

8. Pour exécuter la solution, appuyez sur Ctrl+F5.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
