---
title: Assistant Débogage managé reportAvOnComRelease
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), reference counting errors
- exceptions, reference counting errors
- ReportAvOnComRelease MDA
- COM release access violations
- user reference counting errors
- managed debugging assistants (MDAs), reference counting errors
- report access violation on Com release
- reference counting errors
ms.assetid: a2b86b63-08b2-4943-b344-3c2cf46ccd31
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0bea73a30cb103f0e72caf73a633229a0719dc6c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052329"
---
# <a name="reportavoncomrelease-mda"></a>Assistant Débogage managé reportAvOnComRelease
L'Assistant Débogage managé `reportAvOnComRelease` est activé quand des exceptions sont levées en raison d'erreurs de comptage de références utilisateur pendant une opération COM Interop et l'utilisation de la méthode <xref:System.Runtime.InteropServices.Marshal.Release%2A> ou <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> combinée avec des appels COM bruts.  
  
## <a name="symptoms"></a>Symptômes  
 Violations d'accès et endommagement de la mémoire.  
  
## <a name="cause"></a>Cause  
 Parfois, une exception est levée en raison d'erreurs de comptage de références utilisateur pendant une opération COM Interop et l'utilisation de la méthode <xref:System.Runtime.InteropServices.Marshal.Release%2A> ou <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> combinée avec des appels COM bruts. Normalement, cette exception est ignorée, car elle entraînerait une violation d'accès dans le CLR et l'arrêt de ce dernier. Quand cet Assistant est activé, les exceptions de ce type peuvent être détectées et signalées au lieu d'être simplement ignorées.  
  
## <a name="resolution"></a>Résolution :  
 Examinez votre code de comptage de références, ainsi que les clients natifs de votre objet pour déterminer s'ils contiennent des erreurs de comptage.  
  
## <a name="effect-on-the-runtime"></a>Effet sur le runtime  
 Deux modes sont disponibles. Si l'attribut `allowAv` a pour valeur `true`, l'Assistant empêche le runtime d'ignorer la violation d'accès. Si l'attribut `allowAv` est défini sur `false` (valeur par défaut), le runtime ignore la violation d'accès, mais un message d'avertissement est présenté à l'utilisateur pour indiquer qu'une exception a été levée et ignorée.  
  
## <a name="output"></a>Sortie  
 Si possible, la sortie contient le vtable d'origine du pointeur d'interface COM. Sinon, un message d'information apparaît.  
  
## <a name="configuration"></a>Configuration  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostic d’erreurs avec les Assistants Débogage managé](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling d'interopérabilité](../interop/interop-marshaling.md)
