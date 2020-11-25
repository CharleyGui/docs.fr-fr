---
title: Wrapper pouvant être appelé par le runtime
description: Le CLR expose des objets COM via un wrapper pouvant être appelé par le runtime, qui gère les appels entre un client .NET et un objet COM.
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, COM wrappers
- RCW
- COM wrappers
- runtime callable wrappers
- interoperation with unmanaged code, COM wrappers
ms.assetid: 7e542583-1e31-4e10-b523-8cf2f29cb4a4
ms.openlocfilehash: 985f6e5057a06ac9dcadc0e2c1e4d7743d96f035
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730225"
---
# <a name="runtime-callable-wrapper"></a>Wrapper pouvant être appelé par le runtime

Le common language runtime expose les objets COM via un proxy appelé wrapper RCW. Même si le wrapper RCW est un objet ordinaire pour les clients .NET, sa fonction principale est de marshaler les appels entre un client .NET et un objet COM.  
  
 Le runtime crée un wrapper RCW pour chaque objet COM, quel que soit le nombre de références qui existent sur cet objet. Le runtime gère un seul wrapper RCW par processus pour chaque objet.  Si vous créez un wrapper RCW dans un domaine d'application ou cloisonnement, puis passez une référence à un autre domaine d'application ou cloisonnement, un proxy du premier objet sera utilisé.  Comme le montre l'illustration suivante, il n'existe pas de limite au nombre de clients managés pouvant contenir une référence aux objets COM qui exposent les interfaces INew et INewer.  

L’image suivante montre le processus d’accès aux objets COM par le biais du wrapper RCW :

 ![Processus d’accès aux objets COM par le biais du wrapper RCW.](./media/runtime-callable-wrapper/runtime-callable-wrapper.gif)  

 À l'aide de métadonnées dérivées d'une bibliothèque de types, le runtime crée l'objet COM appelé, ainsi qu'un wrapper pour celui-ci. Chaque wrapper RCW gère un cache de pointeurs d'interface sur l'objet COM qu'il encapsule et libère sa référence à l'objet COM quand le wrapper RCW n'est plus utile. Le runtime exécute le garbage collection du wrapper RCW.  
  
 Entre autres activités, le wrapper RCW marshale les données entre code managé et non managé, pour le compte de l’objet encapsulé. Plus précisément, le wrapper RCW fournit le marshaling pour les arguments de méthode et les valeurs de retour de méthode chaque fois que le client et le serveur ont des représentations différentes des données circulant entre eux.  
  
 Le wrapper standard applique les règles de marshaling intégrées. Par exemple, quand un client .NET passe un type String dans le cadre d’un argument à un objet non managé, le wrapper convertit la chaîne en un type BSTR. Si l'objet COM retourne un BSTR à son appelant managé, l'appelant reçoit une chaîne (String). Le client et le serveur envoient et reçoivent des données qui leur sont familières. Les autres types ne nécessitent pas de conversion. Par exemple, un wrapper standard passera toujours un entier de 4 octets d'un code managé à un code non managé sans convertir le type.  
  
## <a name="marshaling-selected-interfaces"></a>Marshaling d’interfaces sélectionnées  

 L’objectif principal du [wrapper RCW](runtime-callable-wrapper.md) est de masquer les différences entre les modèles de programmation managé et non managé. Pour créer une transition transparente, le wrapper RCW consomme les interfaces COM sélectionnées sans les exposer au client .NET, comme indiqué dans l'illustration suivante.

 L’image suivante montre les interfaces COM et le wrapper RCW :
  
 ![Capture d’écran du wrapper RCW avec des interfaces.](./media/runtime-callable-wrapper/runtime-callable-wrapper-interfaces.gif)  
  
 Quand il est créé comme un objet à liaison anticipée, le wrapper RCW est un type spécifique. Il implémente les interfaces que l'objet COM implémente et expose les méthodes, les propriétés et les événements des interfaces de l'objet. Dans l’illustration, le wrapper RCW expose l’interface INew, mais consomme les interfaces **IUnknown** et **IDispatch**. De plus, le wrapper RCW expose tous les membres de l'interface INew au client .NET.  
  
 Le wrapper RCW consomme les interfaces répertoriées dans le tableau suivant, qui sont exposées par l'objet qu'il encapsule.  
  
|Interface|Description|  
|---------------|-----------------|  
|**IDispatch**|Pour la liaison tardive aux objets COM via la réflexion.|  
|**IErrorInfo**|Fournit une description textuelle de l’erreur, sa source, un fichier d’aide, un contexte d’aide et le GUID de l’interface ayant défini l’erreur (toujours **GUID_NULL** pour les classes .NET).|  
|**IProvideClassInfo**|Si l’objet COM qui est encapsulé implémente **IProvideClassInfo**, le wrapper RCW extrait les informations de type à partir de cette interface pour fournir une meilleure identité de type.|  
|**IUnknown**|Pour l'identité de l'objet, le forçage de type et la gestion de la durée de vie :<br /><br /> - Identité d’un objet<br />     Le runtime fait la distinction entre les objets COM en comparant la valeur d’interface **IUnknown** pour chaque objet.<br />- Forçage de type<br />     Le wrapper RCW reconnaît la découverte de type dynamique exécutée par la méthode **QueryInterface**.<br />- Gestion de la durée de vie<br />     À l’aide de la méthode **QueryInterface**, le wrapper RCW obtient et conserve une référence à un objet non managé jusqu’à ce que le runtime exécute le garbage collection sur le wrapper, qui libère l’objet non managé.|  
  
 Le wrapper RCW peut éventuellement consommer les interfaces répertoriées dans le tableau suivant, qui sont exposées par l'objet qu'il encapsule.  
  
|Interface|Description|  
|---------------|-----------------|  
|**IConnectionPoint** et **IConnectionPointContainer**|Le wrapper RCW convertit les objets qui exposent le style d'événement point de connexion en événements basés sur le délégué.|  
|**IDispatchEx** (.NET Framework uniquement) |Si la classe implémente **IDispatchEx**, le wrapper RCW implémente **IExpando**. L’interface **IDispatchEx** est une extension de l’interface **IDispatch** qui, contrairement à l’interface **IDispatch**, permet l’énumération, l’ajout, la suppression et l’appel de la casse des membres.|  
|**IEnumVARIANT**|Permet aux types COM qui prennent en charge les énumérations d'être traités comme des collections.|  
  
## <a name="see-also"></a>Voir aussi

- [Wrappers COM](com-wrappers.md)
- [Wrapper CCW (COM Callable Wrapper)](com-callable-wrapper.md)
- [Récapitulatif de la conversion d’une bibliothèque de types en assembly](/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Importation d'une bibliothèque de types sous la forme d'un assembly](../../framework/interop/importing-a-type-library-as-an-assembly.md)
