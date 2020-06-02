---
title: Résolution des ressources externes
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ad3fa320-4b8f-4e5c-b549-01157591007a
ms.openlocfilehash: 82e9231be8a3619f59313460f0d5e0b246eb9436
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291485"
---
# <a name="resolving-external-resources"></a>Résolution des ressources externes
La propriété **XmlResolver** de **XmlDocument** est utilisée par la classe **XmlDocument** pour localiser des ressources qui ne sont pas incluses dans les données XML, comme des définitions de type de document (DTD), des entités et des schémas externes. Ces éléments peuvent être localisés sur un réseau ou un lecteur local et sont identifiables par un URI (Uniform Resource Identifier). **XmlDocument** peut ainsi résoudre les nœuds **EntityReference** présents dans le document et valider le document en fonction de la DTD ou du schéma externe.  
  
## <a name="fully-trusted-xmldocument"></a>XmlDocument d'une confiance suffisante  
 La propriété **XmlResolver** affecte la fonctionnalité de la méthode **XmlDocument.Load**. Le tableau suivant montre comment la propriété **XmlDocument.XmlResolver** fonctionne lorsque l'objet **XmlDocument** est entièrement fiable. Le tableau suivant illustre les méthodes **XmlDocument.Load** lorsque l'entrée de Load est **TextReader**, **String**, **Stream** ou **URI**. Ce tableau ne s'applique pas à la méthode **Load** si **XmlDocument** est chargé depuis un **XmlReader**.  
  
|XmlResolver, propriété|Fonction|Notes|  
|--------------------------|--------------|-----------|  
|La propriété est définie sur une classe **XmlResolver** créée précédemment et possède des propriétés déjà définies par l'utilisateur.|Le **XmlDocument** utilise le **XmlResolver** donné pour résoudre des noms de fichiers ainsi que des références aux ressources externes comme par exemple des DTD, des entités et des schémas.<br /><br /> **XmlResolver** est également utilisé pour la résolution des ressources externes nécessaires lors de l'addition ou de la modification de nœuds dans **XmlDocument**.|Le **XmlResolver** donné à **XmlDocument** est le programme de résolution utilisé à chaque fois que des ressources externes doivent être localisées et résolues.|  
|La propriété a la valeur **null** (**Nothing** dans Microsoft Visual Basic .NET).|Les fonctionnalités qui nécessitent une ressource externe ne sont pas prises en charge comme la localisation d’un schéma ou DTD externe. Les entités externes ne seront pas non plus résolues et les fonctions de modification, comme l’insertion de nœuds d’entité qui demandent une résolution, ne sont pas prises en charge.|**XmlDocument** charge des fichiers de manière anonyme et ne cherche pas à résoudre d'autres ressources.|  
|La propriété n'est pas définie, elle reste dans son état par défaut.|Un **XmlUrlResolver** avec des informations d'identification NULL sera instancié et utilisé par **XmlDocument** lors de la résolution de noms de fichiers, de la localisation des DTD, des entités et des schémas externes ; des informations d'identification **null** sont également utilisées lors de la modification des nœuds.||  
  
 Le tableau suivant illustre la méthode **XmlDocument.Load** lorsque l'entrée de **Load** est **XmlReader** et que **XmlDocument** est entièrement fiable.  
  
|XmlResolver, propriété|Fonction|Notes|  
|--------------------------|--------------|-----------|  
|La classe **XmlResolver** utilisée par **XmlDocument** correspond à la même classe utilisée par **XmlReader**.|Le **XmlDocument** utilise le **XmlResolver** assigné à **XmlReader**.<br /><br /> La propriété **XmlDocument.Resolver** ne peut pas être définie, quel que soit le niveau de confiance de **XmlDocument**, car elle reçoit un **XmlResolver** de **XmlReader**. Vous ne pouvez pas essayer de substituer les paramètres **XmlResolver** de **XmlReader** en définissant la propriété **XmlResolver** du **XmlDocument**.|Le **XmlReader** peut être le **XmlTextReader**, **XmlValidatingReader** ou un lecteur à l'écriture personnalisée. Si le lecteur utilisé prend en charge la résolution d’entité, les entités externes sont résolues. Si le lecteur passé ne prend pas en charge les références d'entité, dans ce cas celles-ci ne sont pas résolues.|  
  
## <a name="semi-trusted-xmldocument"></a>XmlDocument d'une confiance partielle  
 Le tableau suivant montre comment la propriété **XmlDocument.XmlResolver** fonctionne lorsque l'objet est d'un niveau de confiance partiel. Ce tableau s'applique aux méthodes**XmlDocument.Load** lorsque l'entrée de Load est **TextReader**, **String**, **Stream** ou **URI**. Ce tableau ne s'applique pas à la méthode **Load** si **XmlDocument** est chargé depuis un **XmlReader**.  
  
|XmlResolver, propriété|Fonction|Notes|  
|--------------------------|--------------|-----------|  
|Dans le scénario d'un niveau de confiance partiel, la propriété **XmlResolver** ne peut pas être définie d'une autre manière que null.|Un **XmlUrlResolver** avec des informations d’identification **null** sera instancié et utilisé par **XmlDocument** lors de la résolution des noms de fichiers, de la localisation des DTD, des entités et des schémas externes, et les informations d’identification **null** sont utilisées lors de la modification des nœuds.|Ce comportement est identique au comportement où la propriété **XmlResolver** n'est pas définie, mais laissée dans son état par défaut.<br /><br /> **XmlDocument** utilise des autorisations anonymes pour toutes les actions.|  
|La propriété a la valeur **null** (**Nothing** dans Microsoft Visual Basic .NET).|Aucune fonctionnalité qui nécessite une ressource externe n'est prise en charge comme la localisation d'un schéma ou DTD externe. Les entités externes ne seront pas non plus résolues et les fonctions de modification, comme l’insertion de nœuds d’entité qui demandent une résolution, ne sont pas prises en charge.|Lorsque la propriété est **null**, le comportement est le même, que **XmlDocument** soit d'un niveau de confiance parfait ou suffisant.|  
|La propriété n'est pas définie, elle reste dans son état par défaut.|Un **XmlUrlResolver** avec des informations d’identification **null** sera instancié et utilisé par **XmlDocument** lors de la résolution des noms de fichiers, de la localisation des DTD, des entités et des schémas externes, et les informations d’identification **null** sont utilisées lors de la modification des nœuds.|**XmlDocument** utilise des autorisations anonymes pour toutes les actions.|  
  
 Ce tableau s'applique à la méthode **XmlDocument.Load** lorsque l'entrée de **Load** est **XmlReader** et que **XmlDocument** est d'un niveau de confiance partiel.  
  
|XmlResolver, propriété|Fonction|Notes|  
|--------------------------|--------------|-----------|  
|La classe **XmlResolver** utilisée par **XmlDocument** correspond à la même classe utilisée par **XmlReader**.|Le **XmlDocument** utilise le **XmlResolver** assigné à **XmlReader**.<br /><br /> La propriété **XmlDocument.Resolver** ne peut pas être définie, quel que soit le niveau de confiance de **XmlDocument**, car elle reçoit un **XmlResolver** de **XmlReader**. Vous ne pouvez pas essayer de substituer les paramètres **XmlResolver de ** **XmlReader** en définissant la propriété **XmlResolver** du **XmlDocument**.|Le **XmlReader** peut être le **XmlTextReader**, l'objet de validation <xref:System.Xml.XmlReader> ou un lecteur à l'écriture personnalisée. Si le lecteur utilisé prend en charge la résolution d’entité, les entités externes sont résolues. Si le lecteur passé ne prend pas en charge de références d'entité, dans ce cas celles-ci ne sont pas résolues.|  
  
 Le paramétrage de XmlResolver pour contenir les informations d'identification correctes permet d'accéder à des ressources externes.  
  
> [!NOTE]
> Il n'existe aucun moyen de récupérer la propriété **XmlResolver**. Cela permet d'éviter qu'un utilisateur ne réutilise un **XmlResolver** sur lequel des informations d'identification ont été définies. De plus, si un **XmlTextReader** ou un objet de validation <xref:System.Xml.XmlReader> est utilisé pour charger **XmlDocument** et si un programme de résolution a été défini sur le **XmlDocument**, les programmes de résolution de ces lecteurs ne sont pas mis en cache par **XmlDocument** après la phase **Load**, dans la mesure où cela présente également un risque pour la sécurité.  
  
 Pour plus d'informations, consultez la section Notes de la page de référence <xref:System.Xml.XmlResolver>.  
  
## <a name="see-also"></a>Voir aussi

- [DOM (Document Object Model) XML](xml-document-object-model-dom.md)
