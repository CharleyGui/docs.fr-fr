---
title: Création et levée d'exceptions - Guide de programmation C#
description: En savoir plus sur la création et la levée d’exceptions. Les exceptions sont utilisées pour indiquer qu’une erreur s’est produite lors de l’exécution d’un programme.
ms.date: 12/09/2020
helpviewer_keywords:
- catching exceptions [C#]
- throwing exceptions [C#]
- exceptions [C#], creating
- exceptions [C#], throwing
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
ms.openlocfilehash: a6998c5b274736b290460808ad4c7cb22be7ebf6
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110206"
---
# <a name="creating-and-throwing-exceptions-c-programming-guide"></a>Création et levée d'exceptions (Guide de programmation C#)

Les exceptions sont utilisées pour indiquer qu’une erreur s’est produite pendant l’exécution du programme. Les objets d’exception qui décrivent une erreur sont créés, puis *levés* avec le mot clé [throw](../../language-reference/keywords/throw.md). Le runtime recherche ensuite le gestionnaire d’exceptions le plus compatible.

Les programmeurs doivent lever des exceptions quand une ou plusieurs des conditions suivantes sont vérifiées :

- La méthode ne peut pas terminer ses fonctionnalités définies. Par exemple, si un paramètre d’une méthode a une valeur non valide :
  :::code language="csharp" source="snippets/exceptions/Program.cs" ID="CantComplete":::
- Un appel inapproprié à un objet est effectué en fonction de l’état de l’objet. Une tentative d’écriture dans un fichier en lecture seule en est un exemple. Dans les cas où l’état d’un objet n’autorise pas une opération, levez une instance de <xref:System.InvalidOperationException> ou un objet basé sur une dérivation de cette classe. Le code suivant est un exemple d’une méthode qui lève un <xref:System.InvalidOperationException> objet :
  :::code language="csharp" source="snippets/exceptions/ProgramLog.cs" ID="ProgramLog":::
- Quand un argument d’une méthode provoque une exception. Dans ce cas, l’exception d’origine doit être interceptée et une instance d’<xref:System.ArgumentException> doit être créée. L’exception d’origine doit être passée au constructeur d’<xref:System.ArgumentException> comme paramètre <xref:System.Exception.InnerException%2A> :
  :::code language="csharp" source="snippets/exceptions/Program.cs" ID="InvalidArg":::

Les exceptions contiennent une propriété nommée <xref:System.Exception.StackTrace%2A>. Cette chaîne contient le nom des méthodes sur la pile des appels actuelle, avec le nom de fichier et le numéro de ligne où l’exception a été levée pour chaque méthode. Un objet <xref:System.Exception.StackTrace%2A> est créé automatiquement par le CLR (Common Language Runtime) à partir du point de l’instruction `throw`, de sorte que les exceptions doivent être levées à partir du point où la trace de la pile doit commencer.

Toutes les exceptions contiennent une propriété nommée <xref:System.Exception.Message%2A>. Cette chaîne doit être définie pour expliquer la raison de l’exception. Les informations sensibles à la sécurité ne doivent pas être placées dans le texte du message. Outre <xref:System.Exception.Message%2A>, <xref:System.ArgumentException> contient une propriété nommée <xref:System.ArgumentException.ParamName%2A> dont la valeur doit être le nom de l’argument qui a provoqué la levée de l’exception. Dans un accesseur Set de propriété, <xref:System.ArgumentException.ParamName%2A> doit avoir la valeur `value` .

Les méthodes publiques et protégées lèvent des exceptions chaque fois qu’elles ne peuvent pas terminer leurs fonctions prévues. La classe d’exception levée est l’exception la plus spécifique disponible qui correspond aux conditions d’erreur. Ces exceptions doivent être documentées dans le cadre de la fonctionnalité de la classe. De plus, les classes dérivées ou les mises à jour de la classe d’origine doivent conserver le même comportement afin d’assurer la compatibilité descendante.

## <a name="things-to-avoid-when-throwing-exceptions"></a>Pratiques à éviter lors de la levée d’exceptions

La liste suivante identifie les pratiques à éviter lors de la levée d’exceptions :

- N’utilisez pas d’exceptions pour modifier le déroulement d’un programme dans le cadre d’une exécution ordinaire. Utilisez des exceptions pour signaler et gérer les conditions d’erreur.
- Les exceptions ne doivent pas être retournées en tant que valeur de retour ou paramètre au lieu d’être levées.
- Ne levez pas <xref:System.Exception?displayProperty=nameWithType> ,, <xref:System.SystemException?displayProperty=nameWithType> <xref:System.NullReferenceException?displayProperty=nameWithType> ou <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> intentionnellement à partir de votre propre code source.
- Ne créez pas d’exceptions qui peuvent être levées en mode débogage, mais pas en mode release. Pour identifier des erreurs d’exécution pendant la phase de développement, utilisez plutôt Debug Assert.

## <a name="defining-exception-classes"></a>Définition de classes d’exceptions

Les programmes peuvent lever une classe d’exceptions prédéfinie dans l’espace de noms <xref:System> (sauf dans les endroits préalablement signalés) ou créer leurs propres classes d’exceptions en les dérivant d’<xref:System.Exception>. Les classes dérivées doivent définir au moins trois constructeurs : un constructeur sans paramètre, un qui définit la propriété du message et un qui définit à la fois la propriété <xref:System.Exception.Message%2A> et la propriété <xref:System.Exception.InnerException%2A>. Le quatrième constructeur est utilisé pour sérialiser l’exception. Les nouvelles classes d’exception doivent être sérialisables. Par exemple :

:::code language="csharp" source="snippets/exceptions/InvalidDepartmentException.cs" id="DefineExceptionClass":::

Ajoutez de nouvelles propriétés à la classe d’exception lorsque les données qu’elles fournissent sont utiles pour résoudre l’exception. Si de nouvelles propriétés sont ajoutées à la classe d’exceptions dérivée, la méthode `ToString()` doit être substituée pour retourner les informations ajoutées.

## <a name="c-language-specification"></a>Spécification du langage C#

Pour plus d’informations, consultez [Exceptions](~/_csharplang/spec/exceptions.md) et [Instruction throw](~/_csharplang/spec/statements.md#the-throw-statement) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.

## <a name="see-also"></a>Voir aussi

- [Hiérarchie des exceptions](../../../standard/exceptions/index.md)
