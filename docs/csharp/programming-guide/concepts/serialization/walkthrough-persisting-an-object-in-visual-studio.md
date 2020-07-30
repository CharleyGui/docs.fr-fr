---
title: 'Procédure pas à pas : persistance d’un objet avec C#'
description: Cet exemple crée un objet Loan de base en C# et conserve ses données dans un fichier, puis crée un nouvel objet avec les données du fichier.
ms.date: 04/26/2018
ms.openlocfilehash: 9f165addc5b9b0d056936458e8529ec1912c417b
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302761"
---
# <a name="walkthrough-persisting-an-object-using-c"></a>Procédure pas à pas : Rendre un objet persistant avec C\#

Vous pouvez utiliser la sérialisation pour rendre les données d’un objet persistantes entre les instances, ce qui vous permet de stocker des valeurs et de les récupérer lors de la prochaine instanciation de l’objet.

Dans cette procédure pas à pas, vous créez un objet `Loan` de base et vous stockez ses données dans un fichier. Vous récupérerez ensuite les données du fichier lors de la recréation de l’objet.

> [!IMPORTANT]
> Cet exemple crée un fichier s’il n’existe pas déjà. Si une application doit créer un fichier, elle doit disposer de l’autorisation `Create` pour le dossier. Les autorisations sont définies à l’aide de listes de contrôle d’accès. Si le fichier existe déjà, l’application a uniquement besoin de l’autorisation `Write`, ce qui représente une autorisation inférieure. Quand c’est possible, il est plus sûr de créer le fichier lors du déploiement et d’accorder l’autorisation `Read` sur un seul fichier (au lieu d’accorder l’autorisation Créer pour un dossier). Par ailleurs, il est plus sûr d’écrire les données dans des dossiers utilisateur que dans le dossier racine ou le dossier Program Files.

> [!IMPORTANT]
> Cet exemple stocke les données dans un fichier au format binaire. Ces formats ne doivent pas être utilisés pour des données sensibles, telles que les mots de passe ou les informations relatives à la carte de crédit.

## <a name="prerequisites"></a>Prérequis

- Pour générer et exécuter, installez le [SDK .NET Core](https://dotnet.microsoft.com/download).

- Installez votre éditeur de code favori, si ce n’est pas déjà fait.

> [!TIP]
> Vous avez besoin d’installer un éditeur de code ? Essayez [Visual Studio](https://visualstudio.com/downloads) !

- L’exemple exige C# 7.3. Voir [Sélectionner la version du langage C#](../../../language-reference/configure-language-version.md).

Vous pouvez examiner l’exemple de code en ligne [sur le référentiel GitHub des exemples .NET](https://github.com/dotnet/samples/tree/master/csharp/serialization).

## <a name="creating-the-loan-object"></a>Création de l’objet loan

La première étape consiste à créer une classe `Loan` et une application console qui utilise cette classe :

1. Créez une application. Tapez `dotnet new console -o serialization` pour créer une application console dans un sous-répertoire nommé `serialization`.
1. Ouvrez l’application dans votre éditeur, et ajoutez une nouvelle classe nommée `Loan.cs`.
1. Ajoutez le code suivant à la classe `Loan` :

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#1)]

Vous devez également créer une application simple qui utilise la classe `Loan`.

## <a name="serialize-the-loan-object"></a>Sérialiser l’objet loan

1. Ouvrez `Program.cs`. Ajoutez le code suivant :

[!code-csharp[Create a loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#1)]

Ajoutez un gestionnaire d’événements pour l’événement `PropertyChanged`, ainsi que quelques lignes pour modifier l’objet `Loan` et afficher les modifications. Vous pouvez voir les ajouts dans le code suivant :

[!code-csharp[Listening for the PropertyChanged event](../../../../../samples/snippets/csharp/serialization/Program.cs#2)]

À ce stade, vous pouvez exécuter le code et voir la sortie actuelle :

```console
New customer value: Henry Clay
7.5
7.1
```

L’exécution de cette application à plusieurs reprises écrit toujours les mêmes valeurs. Un nouvel objet Loan est créé chaque fois que vous exécutez le programme. Dans la réalité, les taux d’intérêt changent régulièrement, mais pas nécessairement chaque fois que l’application est exécutée. Un code de sérialisation signifie que vous conservez le taux d’intérêt le plus récent entre les instances de l’application. C’est ce que vous ferez à l’étape suivante, en ajoutant la sérialisation à la classe Loan.

## <a name="using-serialization-to-persist-the-object"></a>Utilisation de la sérialisation pour rendre l’objet persistant

Pour rendre les valeurs de la classe Loan persistantes, vous devez d’abord marquer la classe avec l’attribut `Serializable`. Ajoutez le code suivant au-dessus de la déclaration de la classe Loan :

[!code-csharp[Loan class definition](../../../../../samples/snippets/csharp/serialization/Loan.cs#2)]

<xref:System.SerializableAttribute> indique au compilateur que tout ce que contient la classe peut être stocké dans un fichier. Étant donné que l’événement `PropertyChanged` ne représente pas une partie du graphe d’objets qui doit être stocké, il ne doit pas être sérialisé. Procéder ainsi sérialiserait tous les objets qui sont attachés à cet événement. Vous pouvez ajouter <xref:System.NonSerializedAttribute> à la déclaration du champ pour le gestionnaire d’événements `PropertyChanged`.

[!code-csharp[Disable serialization for the event handler](../../../../../samples/snippets/csharp/serialization/Loan.cs#3)]

À compter de C# 7.3, vous pouvez attacher des attributs au champ de stockage d’une propriété implémentée automatiquement en utilisant la valeur cible `field`. Le code suivant ajoute une propriété `TimeLastLoaded` et la marque comme non sérialisable :

[!code-csharp[Disable serialization for an auto-implemented property](../../../../../samples/snippets/csharp/serialization/Loan.cs#4)]

L’étape suivante consiste à ajouter le code de sérialisation à l’application LoanApp. Pour sérialiser la classe et l’écrire dans un fichier, vous utilisez les espaces de noms <xref:System.IO> et <xref:System.Runtime.Serialization.Formatters.Binary>. Pour éviter de taper les noms qualifiés complets, vous pouvez ajouter des références aux espaces de noms nécessaires, comme illustré dans le code suivant :

[!code-csharp[Adding namespaces for serialization](../../../../../samples/snippets/csharp/serialization/Program.cs#3)]

L’étape suivante consiste à ajouter le code permettant de désérialiser l’objet à partir du fichier lors de la création de l’objet. Ajoutez une constante à la classe pour le nom de fichier des données sérialisées, comme illustré dans le code suivant :

[!code-csharp[Define the name of the saved file](../../../../../samples/snippets/csharp/serialization/Program.cs#4)]

Ensuite, ajoutez le code suivant après la ligne qui crée l’objet `TestLoan` :

[!code-csharp[Read from a file if it exists](../../../../../samples/snippets/csharp/serialization/Program.cs#5)]

Vous devez d’abord vérifier que le fichier existe. S’il existe, créez une classe <xref:System.IO.Stream> pour lire le fichier binaire et une classe <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> pour convertir le fichier. Vous devez également convertir le type de flux en type d’objet Loan.

Vous devez ensuite ajouter du code pour sérialiser la classe dans un fichier. Ajoutez le code suivant après le code existant de la méthode `Main` :

[!code-csharp[Save the existing Loan object](../../../../../samples/snippets/csharp/serialization/Program.cs#6)]

À ce stade, vous pouvez de nouveau générer et exécuter l’application. La première fois qu’elle s’exécute, notez que le taux d’intérêt commence à 7,5, puis qu’il passe à 7,1. Fermez l’application et exécutez-la de nouveau. L’application indique maintenant qu’elle a lu le fichier enregistré, et le taux d’intérêt est de 7,1 même avant le code qui le change.

## <a name="see-also"></a>Voir aussi

- [Sérialisation (C#)](index.md)
- [Guide de programmation C#](../../index.md)
