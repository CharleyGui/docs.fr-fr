---
title: x:Code, type XAML intrinsèque
ms.date: 03/30/2017
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
ms.openlocfilehash: 7312c59cdcddfdbda39a4a9f05788b6a021f9b75
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459592"
---
# <a name="xcode-intrinsic-xaml-type"></a>x:Code, type XAML intrinsèque
Autorise le positionnement du code dans une production XAML. Ce code peut être compilé par n’importe quelle implémentation de processeur XAML qui compile XAML, ou laissé dans la production XAML pour des utilisations ultérieures telles que l’interprétation par un Runtime.  
  
## <a name="xaml-object-element-usage"></a>Utilisation d'éléments objet XAML  
  
```xaml  
<x:Code>  
   // code instructions, usually enclosed by CDATA...  
</x:Code>  
```  
  
## <a name="remarks"></a>Notes  
 Le code contenu dans l’élément de directive XAML `x:Code` est toujours interprété dans l’espace de noms XML général et dans les espaces de noms XAML fournis. Par conséquent, il est généralement nécessaire de placer le code utilisé pour `x:Code` à l’intérieur d’un segment `CDATA`.  
  
 `x:Code` n’est pas autorisé pour tous les mécanismes de déploiement possibles d’une production XAML. Dans des frameworks spécifiques (par exemple WPF), le code doit être compilé. Dans d’autres infrastructures, l’utilisation de `x:Code` peut être généralement interdite.  
  
 Pour les infrastructures qui autorisent le contenu de `x:Code` managé, le compilateur de langage approprié à utiliser pour le contenu `x:Code` est déterminé par les paramètres et les cibles du projet conteneur utilisé pour compiler l’application.  
  
## <a name="wpf-usage-notes"></a>Remarques sur l’utilisation de WPF  
 Le code déclaré dans `x:Code` pour WPF présente plusieurs limitations notables :  
  
- L’élément de directive `x:Code` doit être un élément enfant immédiat de l’élément racine de la production XAML.  
  
- la [directive x :Class](x-class-directive.md) doit être fournie sur l’élément racine parent.  
  
- Le code placé dans `x:Code` sera traité par compilation pour se trouver dans la portée de la classe partielle qui est déjà en cours de création pour cette page XAML. Par conséquent, tout le code que vous définissez doit être membre ou variables de cette classe partielle.  
  
- Vous ne pouvez pas définir des classes supplémentaires, à l’exception de l’imbrication d’une classe à l’intérieur de la classe partielle (l’imbrication est autorisée, mais elle n’est pas courante, car les classes imbriquées ne peuvent pas être référencées en XAML). Les espaces de noms CLR autres que l’espace de noms utilisé pour la classe partielle existante ne peuvent pas être définis ou ajoutés à.  
  
- Les références aux entités de code en dehors de l’espace de noms CLR de la classe partielle doivent toutes être qualifiées complètes. Si les membres déclarés sont substitués aux membres substituables de classe partielle, il doit être spécifié avec le mot clé de substitution spécifique au langage. Si les membres déclarés dans `x:Code` portée sont en conflit avec les membres de la classe partielle créée à partir du code XAML, de telle sorte que le compilateur signale le conflit, le fichier XAML ne peut pas être compilé ou chargé.  
  
## <a name="see-also"></a>Voir aussi

- [x:Class, directive](x-class-directive.md)
- [Code-behind et XAML dans WPF](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [Vue d’ensemble du langage XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md)
