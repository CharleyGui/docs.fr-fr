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
ms.openlocfilehash: 4da72ed630c1df001e3fd6c7e55f866b94c4d9b1
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071555"
---
# <a name="xcode-intrinsic-xaml-type"></a>x:Code, type XAML intrinsèque
Permet le placement du code dans une production XAML. Ce code peut être compilé par n’importe quelle implémentation de processeur XAML qui compile XAML, soit laissé dans la production XAML pour des utilisations ultérieures telles que l’interprétation par un temps d’exécution.

## <a name="xaml-object-element-usage"></a>Utilisation d'éléments objet XAML

```xaml
<x:Code>
   // code instructions, usually enclosed by CDATA...
</x:Code>
```

## <a name="remarks"></a>Notes

Le code `x:Code` dans l’élément de directive XAML est toujours interprété dans l’espace de nom XML général et les espaces de nom XAML fournis. Par conséquent, il est généralement nécessaire `x:Code` d’enfermer le code utilisé à l’intérieur d’un `CDATA` segment.

`x:Code`n’est pas autorisé pour tous les mécanismes de déploiement possibles d’une production XAML. Dans des cadres spécifiques (par exemple WPF), le code doit être compilé. Dans d’autres `x:Code` cadres, l’utilisation peut généralement être refusée.

Pour les cadres `x:Code` qui permettent le contenu géré, `x:Code` le compilateur de langage correct à utiliser pour le contenu est déterminé par les paramètres et les cibles du projet contenant qui est utilisé pour compiler l’application.

## <a name="wpf-usage-notes"></a>Remarques sur l'utilisation de WPF

Le code `x:Code` déclaré à l’intérieur du FPM comporte plusieurs limites notables :

- L’élément `x:Code` directive doit être un élément enfant immédiat de l’élément racine de la production XAML.

- [x : La directive de classe](xclass-directive.md) doit être fournie sur l’élément racine parent.

- Le code `x:Code` placé à l’intérieur sera traité par compilation pour être dans le cadre de la classe partielle qui est déjà en cours de création pour cette page XAML. Par conséquent, tout le code que vous définissez doit être membre ou variables de cette classe partielle.

- Vous ne pouvez pas définir des classes supplémentaires, sauf en nicher une classe à l’intérieur de la classe partielle (la nidification est autorisée, mais elle n’est pas typique parce que les classes imbriquées ne peuvent pas être référencées dans XAML). Les espaces de noms CLR autres que l’espace nom qui est utilisé pour la classe partielle existante ne peuvent pas être définis ou ajoutés.

- Les références à des entités de code en dehors de l’espace de nom CLR de classe partielle doivent toutes être entièrement qualifiées. Si les membres déclarés remplacent les membres de la classe partielle, cela doit être spécifié avec le mot clé de substitution spécifique à la langue. Si les `x:Code` membres déclarés en conflit de portée avec les membres de la classe partielle créé à partir de la XAML, de telle sorte que le compilateur signale le conflit, le fichier XAML ne peut pas compiler ou charger.

## <a name="see-also"></a>Voir aussi

- [x:Class, directive](xclass-directive.md)
- [Code-behind et XAML dans WPF](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [Vue d’ensemble du langage XAML (WPF)](../fundamentals/xaml.md)
