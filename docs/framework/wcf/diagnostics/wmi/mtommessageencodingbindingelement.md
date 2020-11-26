---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: b4d8503543c93d0112fc39e4b2dba5434bc56472
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96237402"
---
# <a name="mtommessageencodingbindingelement"></a>MtomMessageEncodingBindingElement

MtomMessageEncodingBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>Méthodes  

 La classe MtomMessageEncodingBindingElement ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  

 La classe MtomMessageEncodingBindingElement a les propriétés suivantes :  
  
### <a name="encoding"></a>Encodage  

 Type de données : chaîne  
  
 Type d'accès : Lecture seule  
  
 Encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.  
  
### <a name="maxreadpoolsize"></a>MaxReadPoolSize  

 Type de données : sint32  
  
 Type d'accès : Lecture seule  
  
 Entier qui définit combien de messages peuvent être lus de manière simultanée sans allouer de nouveaux lecteurs.  
  
### <a name="maxwritepoolsize"></a>MaxWritePoolSize  

 Type de données : sint32  
  
 Type d'accès : Lecture seule  
  
 Entier qui définit combien de messages peuvent être envoyés simultanément sans allouer de nouveaux enregistreurs.  
  
### <a name="readerquotas"></a>ReaderQuotas  

 Type de données : XmlDictionaryReaderQuotas  
  
 Type d'accès : Lecture seule  
  
 Quotas des lecteurs.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
