---
title: Extensibilité des liaisons
ms.date: 03/30/2017
ms.assetid: cabdd583-ddf5-493e-9dba-c6c31cde8f65
ms.openlocfilehash: c99713416181aed8a8800c819e0f5786411187ab
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283599"
---
# <a name="binding-extensibility"></a>Extensibilité des liaisons

Cette section contient des exemples qui illustrent la liaison personnalisée dans Windows Communication Foundation (WCF).  
  
## <a name="in-this-section"></a>Dans cette section  

 <xref:System.ServiceModel.NetHttpBinding>  
 Montre comment implémenter une liaison qui empile <xref:System.ServiceModel.Channels.HttpTransportBindingElement> ou le <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> au-dessus du <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>.  
  
 [WSStreamedHttpBinding](wsstreamedhttpbinding.md)  
 Montre comment créer une liaison conçue pour prendre en charge des scénarios de diffusion en continu lorsque le transport HTTP est utilisé.  
