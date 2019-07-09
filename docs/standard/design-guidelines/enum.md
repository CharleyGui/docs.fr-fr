---
title: Conception d'énumérations
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
author: KrzysztofCwalina
ms.openlocfilehash: e890ebbbeb04ca424b84c11791e5ce7fa55db72e
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663480"
---
# <a name="enum-design"></a>Conception d'énumérations

Les enums sont un type spécial de type valeur. Il existe deux types d’énumérations : les enums enums et indicateur simples.

Énumérations simples représentent des petits ensembles fermés de choix. Un exemple courant de l’enum simple est un jeu de couleurs.

Énumérations d’indicateur sont conçues pour prendre en charge des opérations au niveau du bit sur les valeurs d’énumération. Un exemple courant de l’énumération d’indicateurs est une liste d’options.

**✓ DO** permet un enum de type fort aux paramètres, propriétés et retourner des valeurs qui représentent les ensembles de valeurs.

**✓ DO** sont favorables à l’aide d’un enum au lieu de constantes statiques.

**X DO NOT** utiliser un enum pour les ensembles ouverts (par exemple, la version du système d’exploitation, les noms de vos amis, un etc.).

**X DO NOT** fournissent des valeurs d’enum réservé qui sont destinés à un usage ultérieur.

Vous pouvez toujours simplement ajouter des valeurs à l’énumération existante à un stade ultérieur. Consultez [Ajout de valeurs aux Enums](#add_value) pour plus d’informations sur l’ajout de valeurs aux enums. Simplement les valeurs réservées polluent l’ensemble de valeurs réelles et ont tendance à provoquer des erreurs de l’utilisateur.

**X AVOID** exposer publiquement des énumérations avec une seule valeur.

Une pratique courante pour assurer une extensibilité future de l’API C consiste à ajouter des paramètres réservés aux signatures de méthode. Ces paramètres réservés peuvent être exprimées en tant qu’énumérations avec une valeur unique par défaut. Cela ne doit pas être effectuée dans les API gérées. La surcharge de méthode permet d’ajouter des paramètres dans les versions futures.

**X DO NOT** inclure des valeurs de sentinelle dans les énumérations.

Même s’ils sont parfois utiles aux développeurs de framework, les valeurs de sentinelle sont confus pour les utilisateurs du framework. Ils sont utilisés pour effectuer le suivi de l’état de l’enum plutôt que d’être une des valeurs à partir de l’ensemble représenté par l’énumération.

**✓ DO** fournir une valeur de zéro sur les énumérations simples.

La valeur, appelez quelque chose comme « None ». Si une telle valeur n’est pas appropriée pour cet enum particulier, la valeur par défaut courante pour l’énumération doit avoir la valeur sous-jacente égale à zéro.

**✓ CONSIDER** à l’aide de <xref:System.Int32> (la valeur par défaut dans la plupart des langages de programmation) en tant que le type sous-jacent d’une énumération, sauf si une des opérations suivantes est vraie :

- L’énumération est une énumération d’indicateurs, et vous disposez de plus de 32 indicateurs ou souhaitez avoir plus d’informations à l’avenir.

- Le type sous-jacent doit être différent de celui <xref:System.Int32> pour simplifier l’interopérabilité avec le code non managé attendu des énumérations de taille différente.

- Un type sous-jacent plus petit entraînerait des économies substantielles dans l’espace. Si vous pensez que l’énumération à utiliser principalement en tant qu’argument pour le flux de contrôle, la taille importe peu. Les économies de taille peuvent être importantes si :

  - Vous pensez que l’énumération à utiliser en tant que champ dans une structure très fréquemment instanciée ou une classe.

  - Vous prévoyez que les utilisateurs à créer des grands tableaux ou collections d’instances de l’enum.

  - Vous prévoyez un grand nombre d’instances de l’énumération à sérialiser.

Pour une utilisation en mémoire, n’oubliez pas que les objets managés sont toujours `DWORD`-alignés, vous devez efficacement plusieurs énumérations ou autres petites structures dans une instance de compresser un enum plus petits avec afin de faire la différence, car la taille du nombre total d’instances est toujours sera arrondie à un `DWORD`.

**✓ DO** nommer les énumérations d’indicateur avec des noms au pluriel ou des expressions nominales et énumérations simples avec des noms au singulier ou des expressions nominales.

**X DO NOT** étendre <xref:System.Enum?displayProperty=nameWithType> directement.

<xref:System.Enum?displayProperty=nameWithType> est un type spécial utilisé par le CLR pour créer des énumérations définies par l’utilisateur. La plupart des langages de programmation fournissent un élément de programmation qui vous permet d’accéder à cette fonctionnalité. Par exemple, en c# le `enum` mot clé est utilisé pour définir une énumération.

<a name="design"></a>

### <a name="designing-flag-enums"></a>Conception énumérations d’indicateur

**✓ DO** appliquer le <xref:System.FlagsAttribute?displayProperty=nameWithType> pour les énumérations d’indicateur. N’appliquez pas cet attribut aux enums simples.

**✓ DO** utiliser des puissances de deux pour les valeurs d’énumération indicateur afin qu’ils peuvent être combinés librement à l’aide de l’opération OR au niveau du bit.

**✓ CONSIDER** fournissant des valeurs enum spécial pour couramment utilisé les combinaisons d’indicateurs.

Opérations de bits sont un concept avancé et ne doivent pas être requises pour des tâches simples. <xref:System.IO.FileAccess.ReadWrite> est un exemple d’une telle valeur spéciale.

**X AVOID** création enums indicateur où certaines combinaisons de valeurs ne sont pas valides.

**X AVOID** à l’aide de valeurs de l’indicateur enum de zéro, sauf si la valeur représente « tous les indicateurs sont effacés » et est nommée de façon appropriée, comme indiqué par l’instruction suivante.

**✓ DO** nom de la valeur zéro des énumérations d’indicateur `None`. Pour une énumération d’indicateur, la valeur doit toujours signifier « tous les indicateurs sont effacés. »

<a name="add_value"></a>

### <a name="adding-value-to-enums"></a>Ajout de valeur aux Enums

Il est très courant pour découvrir que vous avez besoin ajouter des valeurs à un enum une fois que vous l’avez déjà expédié. Il est un problème de compatibilité d’application potentiel que quand la valeur nouvellement ajoutée est retournée à partir d’une API existante, car des applications mal écrites peut ne pas gérer correctement la nouvelle valeur.

**✓ CONSIDER** Ajout de valeurs pour les enums, en dépit d’un léger risque de compatibilité.

Si vous avez des données réelles concernant les incompatibilités d’application a provoqué par des ajouts à un enum, envisagez d’ajouter une nouvelle API qui retourne les valeurs anciennes et nouvelles et déprécier l’ancienne API, qui doit continuer à retourner simplement les anciennes valeurs. Cela garantit que vos applications existantes restent compatibles.

*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

*Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [instructions de conception Framework : Conventions, les idiomes et les modèles pour les bibliothèques .NET réutilisable, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Instructions pour la conception des types](../../../docs/standard/design-guidelines/type.md)
- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
