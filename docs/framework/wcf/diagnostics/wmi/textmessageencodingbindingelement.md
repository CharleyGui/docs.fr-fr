---
title: TextMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
ms.openlocfilehash: 551761af255681dd2c2dbb9e40b7103c95cd2e0a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267219"
---
# <a name="textmessageencodingbindingelement"></a>TextMessageEncodingBindingElement

TextMessageEncodingBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>Méthodes  

 La classe TextMessageEncodingBindingElement ne définit pas de méthodes.  
  
## <a name="properties"></a>Propriétés  

 La classe TextMessageEncodingBindingElement a les propriétés suivantes :  
  
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

- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
