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
ms.openlocfilehash: 3b24bfefd3edb0585e9c6369e9b8151b17151661
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741717"
---
# <a name="enum-design"></a>Conception d'énumérations

Les enums sont un genre spécial de type valeur. Il existe deux types d’énumérations : les énumérations simples et les énumérations d’indicateur.

Les énumérations simples représentent de petits jeux de choix fermés. Un ensemble de couleurs est un exemple courant de l’énumération simple.

Les enums d’indicateur sont conçus pour prendre en charge des opérations au niveau du bit sur les valeurs enum. Une liste d’options est un exemple courant de l’énumération Flags.

✔️ Utilisez une énumération pour fortement taper des paramètres, des propriétés et des valeurs de retour qui représentent des ensembles de valeurs.

✔️ préférez l’utilisation d’une énumération plutôt que de constantes statiques.

❌ n’utilisez pas d’énumération pour les jeux ouverts (tels que la version du système d’exploitation, les noms de vos amis, etc.).

❌ ne fournissent pas de valeurs d’énumération réservées destinées à un usage ultérieur.

Vous pouvez toujours simplement ajouter des valeurs à l’énumération existante à un moment ultérieur. Pour plus d’informations sur l’ajout de valeurs aux enums, consultez [Ajout de valeurs aux enums](#add_value) . Les valeurs réservées polluent simplement l’ensemble des valeurs réelles et ont tendance à entraîner des erreurs de l’utilisateur.

❌ éviter d’exposer publiquement des enums avec une seule valeur.

Une pratique courante pour garantir une extensibilité future des API C consiste à ajouter des paramètres réservés aux signatures de méthode. Ces paramètres réservés peuvent être exprimés comme des enums avec une seule valeur par défaut. Cela ne doit pas être fait dans les API managées. La surcharge de méthode permet d’ajouter des paramètres dans les versions ultérieures.

❌ n’incluez pas de valeurs Sentinel dans les énumérations.

Bien qu’elles soient parfois utiles pour les développeurs d’infrastructure, les valeurs sentinelles sont confuses pour les utilisateurs de l’infrastructure. Ils sont utilisés pour suivre l’état de l’enum au lieu d’être l’une des valeurs de l’ensemble représenté par l’enum.

✔️ fournissez une valeur égale à zéro sur les énumérations simples.

Envisagez d’appeler la valeur comme « None ». Si une telle valeur n’est pas appropriée pour cette énumération particulière, la valeur par défaut la plus courante pour l’énumération doit être assignée à la valeur sous-jacente de zéro.

✔️ envisagez d’utiliser <xref:System.Int32> (valeur par défaut dans la plupart des langages de programmation) comme type sous-jacent d’une énumération, sauf si l’une des conditions suivantes est vraie :

- L’énumération est une énumération d’indicateurs et vous avez plus de 32 indicateurs, ou vous prévoyez d’en avoir plus à l’avenir.

- Le type sous-jacent doit être différent de <xref:System.Int32> pour faciliter l’interopérabilité avec du code non managé qui attend des énumérations de taille différente.

- Un type sous-jacent plus petit entraînerait des économies substantielles dans l’espace. Si vous vous attendez à ce que l’énumération soit principalement utilisée comme argument pour le workflow de contrôle, la taille n’a pas de différence. Les économies de taille peuvent être significatives dans les cas suivants :

  - Vous vous attendez à ce que l’énumération soit utilisée en tant que champ dans une classe ou une structure très fréquemment instanciée.

  - Vous vous attendez à ce que les utilisateurs créent des tableaux ou des collections volumineux des instances d’énumération.

  - Vous vous attendez à ce qu’un grand nombre d’instances de l’énumération soient sérialisées.

Pour l’utilisation en mémoire, sachez que les objets managés sont toujours `DWORD`alignés. par conséquent, vous avez besoin de plusieurs enums ou d’autres petites structures dans une instance pour empaqueter une énumération plus petite avec pour faire une différence, car la taille totale de l’instance est toujours arrondie à un `DWORD`.

✔️ Nommez les énumérations d’indicateur avec des noms au pluriel ou des expressions nominales et des énumérations simples avec des noms au singulier ou des expressions nominales.

❌ n’étendez pas <xref:System.Enum?displayProperty=nameWithType> directement.

<xref:System.Enum?displayProperty=nameWithType> est un type spécial utilisé par le CLR pour créer des énumérations définies par l’utilisateur. La plupart des langages de programmation fournissent un élément de programmation qui vous permet d’accéder à cette fonctionnalité. Par exemple, dans C# le mot clé `enum` est utilisé pour définir une énumération.

<a name="design"></a>

### <a name="designing-flag-enums"></a>Conception d’énumérations d’indicateur

✔️ appliquer les <xref:System.FlagsAttribute?displayProperty=nameWithType> pour marquer les énumérations. N’appliquez pas cet attribut à des énumérations simples.

✔️ Utilisez les puissances de deux pour les valeurs d’énumération d’indicateur afin qu’elles puissent être combinées librement à l’aide de l’opération or au niveau du bit.

✔️ envisagez de fournir des valeurs d’énumération spéciales pour les combinaisons d’indicateurs couramment utilisées.

Les opérations au niveau du bit sont un concept avancé qui ne doit pas être nécessaire pour les tâches simples. <xref:System.IO.FileAccess.ReadWrite> est un exemple de cette valeur spéciale.

❌ éviter de créer des énumérations d’indicateurs où certaines combinaisons de valeurs ne sont pas valides.

❌ Évitez d’utiliser des valeurs d’énumération d’indicateur de zéro, sauf si la valeur représente « tous les indicateurs sont désactivés » et s’il est nommé de manière appropriée, comme indiqué par l’instruction suivante.

✔️ Nommez la valeur zéro des énumérations d’indicateur `None`. Pour une énumération d’indicateur, la valeur doit toujours signifier que « tous les indicateurs sont effacés ».

<a name="add_value"></a>

### <a name="adding-value-to-enums"></a>Ajouter de la valeur aux enums

Il est très courant de découvrir que vous devez ajouter des valeurs à une énumération une fois que vous l’avez déjà livrée. Il y a un problème potentiel de compatibilité des applications lorsque la valeur récemment ajoutée est retournée à partir d’une API existante, car les applications mal écrites peuvent ne pas gérer correctement la nouvelle valeur.

✔️ envisagez d’ajouter des valeurs aux enums, en dépit d’un faible risque de compatibilité.

Si vous avez des données réelles sur les incompatibilités d’application provoquées par des ajouts à une énumération, envisagez d’ajouter une nouvelle API qui retourne les valeurs nouvelles et anciennes, et de déprécier l’ancienne API, qui doit continuer à retourner uniquement les anciennes valeurs. Cela permet de s’assurer que vos applications existantes restent compatibles.

*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Instructions pour la conception des types](../../../docs/standard/design-guidelines/type.md)
- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
