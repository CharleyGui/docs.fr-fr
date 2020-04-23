---
title: Gestion de xml:space en XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], xml:space attribute
- XAML [XAML Services], white-space processing
- xml:space attribute [XAML Services]
- white-space processing [XAML Services]
ms.assetid: 5e1814f0-5b30-43d5-8c88-dede335a89d7
ms.openlocfilehash: 886f906b6d1e3a10920dbf52e36bf76324c5a9f2
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071436"
---
# <a name="xmlspace-handling-in-xaml"></a>Gestion de xml:space en XAML

L’attribut `xml:space` est un attribut XML défini qui déclare le comportement significatif de traitement de l’espace blanc dans un élément d’objet. Ce comportement est pertinent pour tout contenu (texte `xml:space` interne) contenu dans l’élément où est déclaré, et aussi les étendues aux éléments de l’enfant.

## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML

```xaml
<object xml:space="preserve" />
```

 \- ou -

```xaml
<object xml:space="default" />
```

## <a name="remarks"></a>Notes

La définition `xml:space` de l’attribut dans XAML, `xml:space` y compris ses deux valeurs possibles, est dérivée d’un « attribut spécial » par les spécifications W3C pour XML.

La valeur par `xml:space` défaut de l’attribut est la valeur `"default"`littérale . Pour la `"default"`valeur `xml:space` , ou si n’est pas indiqué du tout, le comportement de l’analyse importante de l’espace blanc est la manipulation par défaut, tel que défini dans le sujet [de traitement de l’espace blanc dans XAML](white-space-processing.md).

Pour préserver l’espace blanc `xml:space="preserve"` dans le contenu de l’élément objet, spécifiez sur cet élément d’objet.

Selon la plupart `xml:space` des interprétations, les effets d’attribut et la valeur de l’attribut sont étendues aux éléments de l’enfant.

Pour une discussion complète du traitement de l’espace blanc dans XAML, voir [le traitement de l’espace blanc dans XAML](white-space-processing.md).

## <a name="see-also"></a>Voir aussi

- [Traitement des espaces blancs en XAML](white-space-processing.md)
- [Vue d’ensemble du langage XAML (WPF)](../fundamentals/xaml.md)
