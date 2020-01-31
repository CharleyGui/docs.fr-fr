---
title: Attribution d'un nom à des paramètres
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
ms.openlocfilehash: ebe2e2db4b109057bf576d4e18cfe511c657707e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743830"
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

 ❌ n’utilisez pas d’abréviations ou d’index numériques pour les noms de paramètre de surcharge d’opérateur.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
- [Directives de nommage](../../../docs/standard/design-guidelines/naming-guidelines.md)
