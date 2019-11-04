---
title: Gestion de xml:space en XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 8f860f5ee42b5c1df43c4ec2b1003408bc1c0d8e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458792"
---
# <a name="xmlspace-handling-in-xaml"></a>Gestion de xml:space en XAML
L’attribut `xml:space` est un attribut XML qui déclare le comportement significatif du traitement des espaces blancs dans un élément objet. Ce comportement est pertinent pour tout le contenu (texte interne) contenu dans l’élément où `xml:space` est déclaré, ainsi que les étendues aux éléments enfants.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```xaml  
<object xml:space="preserve" />  
```  
  
 \- ou -  
  
```xaml  
<object xml:space="default" />  
```  
  
## <a name="remarks"></a>Notes  
 La définition de l’attribut `xml:space` en XAML, y compris ses deux valeurs possibles, est dérivée de `xml:space` comme défini comme un « attribut spécial » par les spécifications W3C pour XML.  
  
 La valeur par défaut de l’attribut `xml:space` est la valeur littérale `"default"`. Pour la valeur `"default"`, ou si `xml:space` n’est pas indiqué, le comportement de l’analyse de l’espace blanc significatif est le traitement par défaut, tel que défini dans la rubrique traitement des espaces [blancs en XAML](whitespace-processing-in-xaml.md).  
  
 Pour conserver les espaces blancs dans le contenu de l’élément objet, spécifiez `xml:space="preserve"` sur cet élément objet.  
  
 Dans la plupart des interprétations, les effets de l’attribut `xml:space` et la valeur de l’attribut sont limités aux éléments enfants.  
  
 Pour une présentation complète du traitement des espaces blancs en XAML, consultez [traitement des espaces blancs en XAML](whitespace-processing-in-xaml.md).  
  
## <a name="see-also"></a>Voir aussi

- [Traitement des espaces blancs en XAML](whitespace-processing-in-xaml.md)
- [Vue d’ensemble du langage XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
