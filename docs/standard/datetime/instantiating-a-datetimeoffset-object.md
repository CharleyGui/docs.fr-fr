---
title: Instanciation d'un objet DateTimeOffset
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- instantiating time zone objects
- time zone objects [.NET Framework], instantiation
- DateTimeOffset structure, converting to DateTime
- DateTimeOffset structure, instantiating
ms.assetid: 9648375f-d368-4373-a976-3332ece00c0a
ms.openlocfilehash: c290af0c9cef619000a6620ba35209489856c5b8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281594"
---
# <a name="instantiating-a-datetimeoffset-object"></a>Instanciation d'un objet DateTimeOffset

La <xref:System.DateTimeOffset> structure offre plusieurs manières de créer des <xref:System.DateTimeOffset> valeurs. Un grand nombre d’entre eux correspondent directement aux méthodes disponibles pour instancier de nouvelles <xref:System.DateTime> valeurs, avec des améliorations qui vous permettent de spécifier le décalage de la valeur de date et d’heure par rapport au temps universel coordonné (UTC, Universal Time Coordinated). En particulier, vous pouvez instancier une <xref:System.DateTimeOffset> valeur des manières suivantes :

- À l’aide d’un littéral de date et d’heure.

- En appelant un <xref:System.DateTimeOffset> constructeur.

- En convertissant implicitement une valeur en <xref:System.DateTimeOffset> valeur.

- En analysant la représentation sous forme de chaîne d’une date et d’une heure.

Cette rubrique fournit des informations supplémentaires et des exemples de code qui illustrent ces méthodes d’instanciation de nouvelles <xref:System.DateTimeOffset> valeurs.

## <a name="date-and-time-literals"></a>Littéraux de date et heure

Pour les langages qui le prennent en charge, l’une des méthodes les plus courantes d’instanciation d’une <xref:System.DateTime> valeur consiste à fournir la date et l’heure sous la forme d’une valeur littérale codée en dur. Par exemple, le code Visual Basic suivant crée un <xref:System.DateTime> objet dont la valeur est le 1er janvier 2008, à 10:00 AM.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#1)]

<xref:System.DateTimeOffset>les valeurs peuvent également être initialisées à l’aide de littéraux de date et d’heure lors de l’utilisation de langages qui prennent en charge les <xref:System.DateTime> littéraux. Par exemple, le code Visual Basic suivant crée un <xref:System.DateTimeOffset> objet.

[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#2)]

Comme le montre la sortie de la console, la <xref:System.DateTimeOffset> valeur créée de cette façon se voit assigner le décalage du fuseau horaire local. Cela signifie qu’une <xref:System.DateTimeOffset> valeur affectée à l’aide d’un littéral de caractère n’identifie pas un point unique dans le temps si le code est exécuté sur des ordinateurs différents.

## <a name="datetimeoffset-constructors"></a>Constructeurs DateTimeOffset

Le <xref:System.DateTimeOffset> type définit six constructeurs. Quatre d’entre eux correspondent directement aux <xref:System.DateTime> constructeurs, avec un paramètre supplémentaire de type <xref:System.TimeSpan> qui définit le décalage de date et d’heure par rapport à l’heure UTC. Elles vous permettent de définir une <xref:System.DateTimeOffset> valeur en fonction de la valeur de ses composants individuels de date et d’heure. Par exemple, le code suivant utilise ces quatre constructeurs pour instancier des <xref:System.DateTimeOffset> objets avec des valeurs identiques de 7/1/2008 12:05 AM + 01:00.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#3)]

Notez que, lorsque la valeur de l' <xref:System.DateTimeOffset> objet instancié à l’aide d’un <xref:System.Globalization.PersianCalendar> objet comme l’un des arguments de son constructeur est affichée dans la console, elle est exprimée sous la forme d’une date du calendrier grégorien plutôt que du calendrier persan. Pour générer une date à l’aide du calendrier persan, consultez l’exemple dans la <xref:System.Globalization.PersianCalendar> rubrique.

Les deux autres constructeurs créent un <xref:System.DateTimeOffset> objet à partir d’une <xref:System.DateTime> valeur. Le premier d’entre eux a un seul paramètre, la <xref:System.DateTime> valeur à convertir en <xref:System.DateTimeOffset> valeur. Le décalage de la valeur résultante <xref:System.DateTimeOffset> dépend de la <xref:System.DateTime.Kind%2A> propriété du paramètre unique du constructeur. Si sa valeur est <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> , le décalage est défini comme étant égal à <xref:System.TimeSpan.Zero?displayProperty=nameWithType> . Sinon, son décalage est défini comme égal à celui du fuseau horaire local. L’exemple suivant illustre l’utilisation de ce constructeur pour instancier des <xref:System.DateTimeOffset> objets représentant l’heure UTC et le fuseau horaire local :

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#4)]

> [!NOTE]
> L’appel de la surcharge du <xref:System.DateTimeOffset> constructeur qui a un seul <xref:System.DateTime> paramètre équivaut à effectuer une conversion implicite d’une <xref:System.DateTime> valeur en <xref:System.DateTimeOffset> valeur.

Le deuxième constructeur qui crée un <xref:System.DateTimeOffset> objet à partir d’une <xref:System.DateTime> valeur a deux paramètres : la <xref:System.DateTime> valeur à convertir et une <xref:System.TimeSpan> valeur représentant le décalage de date et d’heure par rapport à l’heure UTC. Cette valeur de décalage doit correspondre à la <xref:System.DateTime.Kind%2A> propriété du premier paramètre du constructeur ou une <xref:System.ArgumentException> exception est levée. Si la <xref:System.DateTime.Kind%2A> propriété du premier paramètre est <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> , la valeur du deuxième paramètre doit être <xref:System.TimeSpan.Zero?displayProperty=nameWithType> . Si la <xref:System.DateTime.Kind%2A> propriété du premier paramètre est <xref:System.DateTimeKind.Local?displayProperty=nameWithType> , la valeur du deuxième paramètre doit correspondre au décalage du fuseau horaire du système local. Si la <xref:System.DateTime.Kind%2A> propriété du premier paramètre est <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> , le décalage peut être n’importe quelle valeur valide. Le code suivant illustre les appels à ce constructeur pour convertir <xref:System.DateTime> en <xref:System.DateTimeOffset> valeurs.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#5)]

## <a name="implicit-type-conversion"></a>Conversion de type implicite

Le <xref:System.DateTimeOffset> type prend en charge une conversion de type implicite : d’une <xref:System.DateTime> valeur à une <xref:System.DateTimeOffset> valeur. (Une conversion de type implicite est une conversion d’un type vers un autre qui ne nécessite pas de cast explicite (en C#) ni de conversion (en Visual Basic), et qui ne perd pas d’informations. Elle permet d’utiliser un code similaire au suivant.)

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#6)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#6)]

Le décalage de la valeur résultante <xref:System.DateTimeOffset> dépend de la valeur de la <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> propriété. Si sa valeur est <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> , le décalage est défini comme étant égal à <xref:System.TimeSpan.Zero?displayProperty=nameWithType> . Si sa valeur est <xref:System.DateTimeKind.Local?displayProperty=nameWithType> ou <xref:System.DateTimeKind.Unspecified?displayProperty=nameWithType> , le décalage est défini comme égal à celui du fuseau horaire local.

## <a name="parsing-the-string-representation-of-a-date-and-time"></a>Analyse de la représentation sous forme de chaîne d’une date et d’une heure

Le <xref:System.DateTimeOffset> type prend en charge quatre méthodes qui vous permettent de convertir la représentation sous forme de chaîne d’une date et d’une heure en une <xref:System.DateTimeOffset> valeur :

- <xref:System.DateTimeOffset.Parse%2A>, qui tente de convertir la représentation sous forme de chaîne d’une date et d’une heure en <xref:System.DateTimeOffset> valeur et lève une exception en cas d’échec de la conversion.

- <xref:System.DateTimeOffset.TryParse%2A>, qui tente de convertir la représentation sous forme de chaîne d’une date et d’une heure en <xref:System.DateTimeOffset> valeur et retourne `false` si la conversion échoue.

- <xref:System.DateTimeOffset.ParseExact%2A>, qui tente de convertir la représentation sous forme de chaîne d’une date et d’une heure dans un format spécifié en une <xref:System.DateTimeOffset> valeur. La méthode lève une exception si la conversion échoue.

- <xref:System.DateTimeOffset.TryParseExact%2A>, qui tente de convertir la représentation sous forme de chaîne d’une date et d’une heure dans un format spécifié en une <xref:System.DateTimeOffset> valeur. La méthode retourne `false` si la conversion échoue.

L’exemple suivant illustre les appels à chacune de ces quatre méthodes de conversion de chaîne pour instancier une <xref:System.DateTimeOffset> valeur.

[!code-csharp[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/cs/Instantiate.cs#7)]
[!code-vb[System.DateTimeOffset.Conceptual.Instantiate#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual.Instantiate/vb/Instantiate.vb#7)]

## <a name="see-also"></a>Voir aussi

- [Dates, heures et fuseaux horaires](index.md)
