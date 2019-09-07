---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: cddd9f0c1dda982c1795500723c21546bd58c92b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399098"
---
# <a name="windowsstreamsecurity"></a>\<windowsStreamSecurity>
Spécifiez les paramètres de sécurité de flux de données Windows pour la liaison personnalisée.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Par windowsStreamSecurity >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|protectionLevel|Définit la sécurité au niveau du message. La signature des messages atténue le risque de modification par un tiers pendant le transfert. Le chiffrement garantit la confidentialité des données pendant le transport. Les valeurs valides sont les suivantes :<br /><br /> None Aucune protection.<br />Expéditeur Les messages sont signés.<br />EncryptAndSign Les messages sont signés et chiffrés.<br /><br /> La valeur par défaut est EncryptAndSign.<br /><br /> Cet attribut est de type <xref:System.Net.Security.ProtectionLevel>.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<binding>](../../../misc/binding.md)|Définit toutes les fonctions de liaison d’une liaison personnalisée.|  
  
## <a name="remarks"></a>Notes  
 Les transports qui utilisent un protocole orienté flux de données, tel que TCP, et des canaux nommés prennent en charge les mises à niveau de transport basées sur le flux de données. Plus spécifiquement, WCF fournit les mises à niveau de la sécurité. La configuration de cette sécurité de transport est encapsulée par cet élément de configuration ainsi que par [ \<section sslStreamSecurity >](sslstreamsecurity.md), qui peut être configuré et ajouté à une liaison personnalisée.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [Liaisons](../../../wcf/bindings.md)
- [Extension de liaisons](../../../wcf/extending/extending-bindings.md)
- [Liaisons personnalisées](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
