---
title: <allowAccounts>
ms.date: 03/30/2017
ms.assetid: 166923a9-a8ac-478f-92f9-529d9667f3a6
ms.openlocfilehash: 74b9d51b7400469c96fc9c8b36e4b0fb1d46969b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398402"
---
# <a name="allowaccounts"></a>\<allowAccounts>
Contient une collection d’éléments de configuration qui spécifient des comptes d’utilisateur pour les processus qui hébergent des services Windows Communication Foundation (WCF) et qui disposent d’un accès de connexion au service de partage.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel. activation >** ](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> net. pipe**](net-pipe.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<allowAccounts >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<allowAccounts>
  <add securityIdentifier="String" />
</allowAccounts>
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun.  
  
### <a name="child-elements"></a>Éléments enfants  
  
|Attribut|Description|  
|---------------|-----------------|  
|[\<add>](add-of-allowaccounts.md)|Ajoute un compte d’utilisateur pour les processus qui hébergent des services WCF et qui disposent d’un accès de connexion au service de partage.|  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|NET. pipe > ou [ \<](net-pipe.md) [ \<net. TCP >](net-tcp.md)|Spécifie les paramètres de configuration pour le canal du réseau ou les services de partage TCP.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>
- <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>
