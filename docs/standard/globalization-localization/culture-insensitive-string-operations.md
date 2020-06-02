---
title: Opérations de chaînes indépendantes de la culture
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture, culture-insensitive string operations
- case-sensitive comparisons
- globalization [.NET Framework], culture-insensitive string operations
- strings [.NET Framework], culture-insensitive string operations
- localization [.NET Framework], culture-insensitive string operations
- world-ready applications, culture-insensitive string operations
- culture-sensitive string operations
- culture-insensitive string operations
ms.assetid: e6e2bb94-a95d-44e2-b68c-cfdd1db77784
ms.openlocfilehash: 0db77f3e11542bb920df1e45312a72decc2a34fd
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279787"
---
# <a name="culture-insensitive-string-operations"></a>Opérations de chaînes indépendantes de la culture

Les opérations de chaînes dépendantes de la culture peuvent présenter un avantage si vous créez des applications conçues pour afficher des résultats en fonction de la culture des utilisateurs. Par défaut, les méthodes dépendantes de la culture obtiennent la culture à utiliser à partir de la propriété <xref:System.Globalization.CultureInfo.CurrentCulture%2A> du thread.

Cependant, les opérations de chaînes dépendantes de la culture ne correspondent pas toujours au comportement souhaité. L'utilisation d'opérations dépendantes de la culture dans des scénarios où les résultats doivent être indépendants de la culture peut entraîner l'échec du code de l'application sur les cultures avec des mappages de casse personnalisés et des règles de tri. Pour obtenir un exemple, consultez la section [« comparaisons de chaînes qui utilisent la culture actuelle »](../base-types/best-practices-strings.md#string-comparisons-that-use-the-current-culture) dans l’article [meilleures pratiques pour l’utilisation de chaînes](../base-types/best-practices-strings.md) .

La manière avec laquelle votre application utilise les résultats détermine si des opérations de chaînes sont dépendantes ou non de la culture. Les opérations de chaînes qui affichent des résultats à l'utilisateur final doivent être généralement dépendantes de la culture. Par exemple, si une application affiche une liste triée de chaînes localisées dans une zone de liste, l'application doit effectuer un tri dépendant de la culture.

Les résultats des opérations de chaînes qui sont utilisés en interne doivent être généralement indépendants de la culture. En général, si l'application utilise des noms de fichiers, des formats de persistance ou des informations symboliques qui ne sont pas affichées, les résultats des opérations de chaînes ne doivent pas varier selon la culture. Par exemple, si une application compare une chaîne pour déterminer si celle-ci est une balise XML reconnue, la comparaison ne doit pas être dépendante de la culture. Si une décision de sécurité est basée sur le résultat d'une opération de comparaison de chaînes ou de changement de casse, cette opération doit être indépendante de la culture pour garantir que le résultat n'est pas affecté par la valeur de <xref:System.Globalization.CultureInfo.CurrentCulture%2A>.

Que vous développiez ou non une application incluant du code pour gérer des problèmes de localisation et de globalisation, vous devez connaître les méthodes de .NET Framework qui retournent les résultats dépendants de la culture par défaut. L'objectif de cette rubrique est d'illustrer d'une manière appropriée l'utilisation de ces méthodes lorsque votre application désire obtenir des résultats indépendants de la culture.

## <a name="see-also"></a>Voir aussi

- [Globalisation et localisation](index.md)
