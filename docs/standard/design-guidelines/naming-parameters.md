---
title: Attribution d'un nom à des paramètres
description: Découvrez les instructions relatives à la dénomination des paramètres. Par exemple, utilisez des noms de paramètres descriptifs & casse mixte, & envisagez d’attribuer un nom en fonction de la signification au lieu de type.
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
ms.openlocfilehash: 54f37c4d6a0f9a6931fa69d612bf0e45bf1f2ce7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84583516"
---
# <a name="naming-parameters"></a>Attribution d'un nom à des paramètres
Au-delà de la raison évidente de la lisibilité, il est important de suivre les instructions pour les noms de paramètres, car les paramètres sont affichés dans la documentation et dans le concepteur quand les outils de conception visuelle proposent IntelliSense et la fonctionnalité de navigation des classes.

 ✔️ Utilisez camelCasing dans les noms de paramètres.

 ✔️ Utilisez des noms de paramètres descriptifs.

 ✔️ envisagez d’utiliser des noms basés sur la signification d’un paramètre plutôt que sur le type du paramètre.

### <a name="naming-operator-overload-parameters"></a>Affectation de noms aux paramètres de surcharge d’opérateur
 ✔️ Utilisez `left` et `right` pour les noms de paramètre de surcharge d’opérateur binaire s’il n’y a aucune signification pour les paramètres.

 ✔️ Utilisez `value` pour les noms de paramètre de surcharge d’opérateur unaire si les paramètres n’ont aucune signification.

 ✔️ CONSIDÉRez les noms significatifs pour les paramètres de surcharge d’opérateur si cela ajoute une valeur significative.

 ❌N’utilisez pas d’abréviations ou d’index numériques pour les noms de paramètre de surcharge d’opérateur.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Directives de conception d’infrastructure](index.md)
- [Instructions d’affectation de noms](naming-guidelines.md)
