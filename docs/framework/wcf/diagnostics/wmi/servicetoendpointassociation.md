---
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: 6e20556541b1aa48e7dfc6a8cde97e1bc477457e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273943"
---
# <a name="servicetoendpointassociation"></a>ServiceToEndpointAssociation

Mappe un service à un point de terminaison.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## <a name="methods"></a>Méthodes  

 La classe ServiceToEndpointAssociation ne définit pas de méthode.  
  
## <a name="properties"></a>Propriétés  

 La classe ServiceToEndpointAssociation a les propriétés suivantes :  
  
### <a name="ref"></a>ref  

 Type de données : service  
  
 Type d'accès : Lecture seule  
Qualificateurs : Clé  
  
 Service associé au point de terminaison.  
  
### <a name="ref"></a>ref  

 Type de données : point de terminaison  
  
 Type d'accès : Lecture seule  
Qualificateurs : Clé  
  
 Point de terminaison associé au service.  
  
## <a name="requirements"></a>Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|
