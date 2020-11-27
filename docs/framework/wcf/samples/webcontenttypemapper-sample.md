---
title: WebContentTypeMapper, exemple
ms.date: 03/30/2017
ms.assetid: a4fe59e7-44d8-43c6-a1f8-40c45223adca
ms.openlocfilehash: 550e763d30a7fa503f6500dcaa8f9b77ea499bca
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283261"
---
# <a name="webcontenttypemapper-sample"></a>WebContentTypeMapper, exemple

Cet exemple montre comment mapper de nouveaux types de contenu à des formats de corps de message Windows Communication Foundation (WCF).  
  
 L' <xref:System.ServiceModel.Description.WebHttpEndpoint> élément se connecte à l’encodeur de message Web, ce qui permet à WCF de recevoir des messages JSON, XML ou binaires bruts au même point de terminaison. L'encodeur détermine le format du corps des messages en examinant le type de contenu HTTP des demandes. Cet exemple introduit la classe <xref:System.ServiceModel.Channels.WebContentTypeMapper>, laquelle permet à l'utilisateur de contrôler le mappage entre le type de contenu et le format du corps des messages.  
  
 WCF fournit un ensemble de mappages par défaut pour les types de contenu. Par exemple, les mappages `application/json` et `text/xml` permettent de mapper les messages aux formats JSON et XML respectivement. Les types de contenu qui ne sont pas mappés aux formats JSON ou XML sont mappés au format binaire brut.  
  
 Dans certaines situations (par exemple, avec des API de type push), les développeurs de service ne contrôlent pas le type de contenu retourné par le client. Par exemple, les clients peuvent retourner le format JSON comme `text/javascript` au lieu de retourner `application/json`. Dans ce cas de figure, le développeur de service doit fournir un type qui dérive de <xref:System.ServiceModel.Channels.WebContentTypeMapper> pour pouvoir gérer correctement ce type de contenu, tel qu'illustré dans l'exemple de code suivant.  
  
```csharp  
public class JsonContentTypeMapper : WebContentTypeMapper  
{  
    public override WebContentFormat  
               GetMessageFormatForContentType(string contentType)  
    {  
        if (contentType == "text/javascript")  
        {  
            return WebContentFormat.Json;  
        }  
        else  
        {  
            return WebContentFormat.Default;  
        }  
    }  
}  
```  
  
 Ce type doit se substituer à la méthode <xref:System.ServiceModel.Channels.WebContentTypeMapper.GetMessageFormatForContentType%28System.String%29>. La méthode doit évaluer l'argument `contentType` et retourner l'une des valeurs suivantes : <xref:System.ServiceModel.Channels.WebContentFormat.Json>, <xref:System.ServiceModel.Channels.WebContentFormat.Xml>, <xref:System.ServiceModel.Channels.WebContentFormat.Raw> ou <xref:System.ServiceModel.Channels.WebContentFormat.Default>. Lorsque cette méthode retourne la valeur <xref:System.ServiceModel.Channels.WebContentFormat.Default>, les mappages d'encodeur de message Web par défaut sont utilisés. Dans l'exemple de code précédent, le type de contenu `text/javascript` est mappé au format JSON. Tous les autres mappages restent, en revanche, inchangés.  
  
 Pour utiliser la classe `JsonContentTypeMapper`, utilisez ce qui suit dans votre Web.config :  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <standardEndpoint name="" contentTypeMapper="Microsoft.Samples.WebContentTypeMapper.JsonContentTypeMapper, JsonContentTypeMapper, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 Pour vérifier les conditions requises à l'utilisation du JsonContentTypeMapper, supprimez l'attribut contentTypeMapper du fichier de configuration ci-dessus. La page du client ne parvient pas à se charger lorsqu'elle essaie d'utiliser `text/javascript` pour envoyer le contenu JSON.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Générez la solution WebContentTypeMapperSample. sln comme décrit dans [génération des exemples de Windows Communication Foundation](building-the-samples.md).  
  
3. Accédez à `http://localhost/ServiceModelSamples/JCTMClientPage.htm` (n’ouvrez pas JCTMClientPage.htm dans le navigateur dans le répertoire du projet).  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Ajax\WebContentTypeMapper`  
