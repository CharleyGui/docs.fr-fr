---
title: Classes et objets – Présentation du tutoriel C#
description: Créez votre premier programme C# et explorez les concepts orientés objet
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: 5edb2d7b11caace2d794b7958dfeb75ef502ee2b
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396861"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a>Explorez la programmation orientée objet avec des classes et des objets

Ce tutoriel suppose que vous disposez d’un ordinateur que vous pouvez utiliser pour le développement. Le didacticiel .NET [Hello World en 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) contient des instructions pour la configuration de votre environnement de développement local sur Windows, Linux ou MacOS. Vous trouverez une brève vue d’ensemble des commandes utilisées dans [Se familiariser avec les outils de développement](local-environment.md), avec des liens vers des informations complémentaires.

## <a name="create-your-application"></a>Créer votre application

Dans une fenêtre de terminal, créez un répertoire nommé *classes*. Vous y créerez votre application. Sélectionnez ce répertoire et tapez `dotnet new console` dans la fenêtre de console. Cette commande crée votre application. Ouvrez *Program.cs*. Il doit se présenter comme suit :

```csharp
using System;

namespace classes
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

Dans ce tutoriel, vous allez créer des types qui représentent un compte bancaire. Les développeurs définissent généralement chaque classe dans un fichier texte différent. Cela simplifie la gestion au fur et à mesure qu’un programme augmente en taille. Créez un fichier nommé *BankAccount.cs* dans le répertoire *classes*.

Ce fichier contiendra la définition d’un ***compte bancaire***. La programmation orientée objet organise le code en créant des types sous la forme de ***classes***. Ces classes contiennent le code qui représente une entité spécifique. La classe `BankAccount` représente un compte bancaire. Le code implémente des opérations spécifiques à travers des méthodes et des propriétés. Dans ce tutoriel, le compte bancaire prend en charge le comportement suivant :

1. Il contient un numéro à 10 chiffres qui identifie le compte bancaire de manière unique.
1. Il contient une chaîne qui stocke le nom du ou des détenteurs.
1. Le solde peut être récupéré.
1. Il accepte les dépôts.
1. Il accepte les retraits.
1. Le solde initial doit être positif.
1. Les retraits ne peuvent pas générer un solde négatif.

## <a name="define-the-bank-account-type"></a>Définir le type de compte bancaire

Vous pouvez commencer par créer les éléments de base d’une classe définissant ce comportement. Créez un nouveau fichier à l’aide de la commande **file : New** . Nommez-le *BankAccount.cs*. Ajoutez le code suivant à votre fichier *BankAccount.cs* :

```csharp
using System;

namespace classes
{
    public class BankAccount
    {
        public string Number { get; }
        public string Owner { get; set; }
        public decimal Balance { get; }

        public void MakeDeposit(decimal amount, DateTime date, string note)
        {
        }

        public void MakeWithdrawal(decimal amount, DateTime date, string note)
        {
        }
    }
}
```

Avant de poursuivre, examinons ce que vous venez de créer.  La déclaration `namespace` permet d’organiser logiquement votre code. Ce tutoriel étant relativement petit, vous allez placer tout le code dans un même espace de noms.

`public class BankAccount` définit la classe ou le type que vous créez. Tout ce qui se trouve à l’intérieur du `{` et `}` qui suit la déclaration de classe définit l’État et le comportement de la classe. La classe `BankAccount` a cinq ***membres***. Les trois premiers sont des ***propriétés***. Les propriétés sont des éléments de données qui peuvent avoir un code qui applique la validation ou d’autres règles. Les deux derniers sont des ***méthodes***. Les méthodes sont des blocs de code qui effectuent une fonction unique. La lecture des noms de chacun des membres doit fournir suffisamment d’informations pour vous permettre (ou à tout autre développeur) de comprendre ce que fait la classe.

## <a name="open-a-new-account"></a>Ouvrir un nouveau compte

La première fonctionnalité à implémenter est l’ouverture d’un compte bancaire. Quand un client ouvre un compte, il doit fournir un solde initial, ainsi que des informations sur le ou les détenteurs du compte.

La création d’un objet du type `BankAccount` suppose la définition d’un ***constructeur*** qui assigne ces valeurs. Un ***constructeur*** est un membre qui porte le même nom que la classe. Il est utilisé pour initialiser des objets de ce type de classe. Ajoutez le constructeur suivant au `BankAccount` type. Placez le code suivant au-dessus de la déclaration de `MakeDeposit` :

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

Les constructeurs sont appelés lorsque vous créez un objet à l’aide de [`new`](../../language-reference/operators/new-operator.md) . Remplacez la ligne `Console.WriteLine("Hello World!");` dans *Program.cs* par le code suivant (remplacez `<name>` par votre nom) :

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

Exécutons ce que vous avez créé jusqu’à présent. Si vous utilisez Visual Studio, sélectionnez exécuter **sans débogage** dans le menu **exécuter** . Si vous utilisez une ligne de commande, tapez `dotnet run` le répertoire dans lequel vous avez créé votre projet.

Avez-vous remarqué que le numéro de compte est vide ? L’heure est venue de traiter ce point. Le numéro de compte doit être assigné une fois l’objet construit. Mais ce ne devrait pas être à l’appelant de le créer. Le code de la classe `BankAccount` devrait savoir comment assigner de nouveaux numéros de compte.  Un moyen simple de le faire consiste à commencer par un numéro à 10 chiffres. Incrémentez-le chaque fois qu’un compte est créé. Enfin, stockez le numéro de compte actuel quand un objet est construit.

Ajoutez une déclaration de membre à la `BankAccount` classe. Placez la ligne de code suivante après l’accolade ouvrante `{` au début de la `BankAccount` classe :

```csharp
private static int accountNumberSeed = 1234567890;
```

Il s’agit d’un membre de données. Celui-ci est `private`, ce qui signifie qu’il est uniquement accessible par code dans la classe `BankAccount`. C’est un moyen de séparer les responsabilités publiques (comme la présence d’un numéro de compte) de l’implémentation privée (comment les numéros de compte sont générés). Il est également `static`, ce qui signifie qu’il est partagé par toutes les objets `BankAccount`. La valeur d’une variable non statique est unique pour chaque instance de l’objet `BankAccount`. Ajoutez les deux lignes suivantes au constructeur pour assigner le numéro de compte. Placez-les après la ligne qui indique `this.Balance = initialBalance` :

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

Tapez `dotnet run` pour afficher les résultats.

## <a name="create-deposits-and-withdrawals"></a>Créer des dépôts et des retraits

La classe de votre compte bancaire doit accepter les dépôts et les retraits pour fonctionner correctement. Nous allons implémenter des dépôts et des retraits en créant un journal de chaque transaction du compte. Ce dernier présente plusieurs avantages par rapport à la simple mise à jour du solde à chaque transaction. L’historique peut être utilisé pour auditer toutes les transactions et gérer les soldes au quotidien. En calculant le solde à partir de l’historique de toutes les transactions lorsque nécessaire, toutes les erreurs d’une même transaction qui sont résolues apparaîtront correctement dans le solde dans le calcul suivant.

Commençons par créer un type pour représenter une transaction. Il s’agit d’un type simple qui n’a aucune responsabilité. Il a besoin de quelques propriétés. Créez un fichier nommé *Transaction.cs*. Ajoutez-lui le code suivant :

[!code-csharp[Transaction](~/samples/snippets/csharp/classes-quickstart/Transaction.cs)]

Nous allons maintenant ajouter une <xref:System.Collections.Generic.List%601> d’objets `Transaction` à la classe `BankAccount`. Ajoutez la déclaration suivante après le constructeur dans votre fichier *BankAccount.cs* :

[!code-csharp[TransactionDecl](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#TransactionDeclaration)]

Avec la classe <xref:System.Collections.Generic.List%601>, vous devez importer un espace de noms différent. Ajoutez le code suivant au début de *BankAccount.cs* :

```csharp
using System.Collections.Generic;
```

Nous allons à présent modifier la façon dont le `Balance` est présenté.  Il peut être obtenu en additionnant les valeurs de toutes les transactions. Modifiez la déclaration de `Balance` dans la classe `BankAccount` comme suit :

[!code-csharp[BalanceComputation](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#BalanceComputation)]

Cet exemple montre un aspect important des ***propriétés***. Vous calculez à présent le solde quand un autre programmeur en demande la valeur. Votre calcul énumère toutes les transactions et retourne la somme en tant que solde actuel.

Implémentez ensuite les méthodes `MakeDeposit` et `MakeWithdrawal`. Ces méthodes appliquent les deux règles finales suivantes : le solde initial doit être positif et un retrait ne doit pas générer de solde négatif.

Cela introduit le concept d’***exceptions***. Le moyen typique d’indiquer qu’une méthode ne peut pas effectuer correctement son travail consiste à lever une exception. Le type d’exception et le message associé décrivent l’erreur. Ici, la méthode `MakeDeposit` lève une exception si le montant du dépôt est négatif. La `MakeWithdrawal` méthode lève une exception si le montant du retrait est négatif ou si l’application du retrait entraîne un solde négatif. Ajoutez le code suivant après la déclaration de la `allTransactions` liste :

[!code-csharp[DepositAndWithdrawal](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#DepositAndWithdrawal)]

L' [`throw`](../../language-reference/keywords/throw.md) instruction **lève** une exception. L’exécution du bloc actuel se termine et le contrôle est transféré au premier bloc correspondant `catch` trouvé dans la pile des appels. Vous ajouterez un bloc `catch` pour tester ce code un peu plus tard.

Le constructeur devrait obtenir une modification lui permettant d’ajouter une transaction initiale au lieu de mettre directement le solde à jour. Étant donné que vous avez déjà écrit la méthode `MakeDeposit`, appelez-la à partir de votre constructeur. Le constructeur terminé doit être semblable à ce qui suit :

[!code-csharp[Constructor](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#Constructor)]

<xref:System.DateTime.Now?displayProperty=nameWithType> est une propriété qui retourne la date et l'heure actuelles. Pour tester cela, ajoutez quelques dépôts et retraits dans votre `Main` méthode, à la suite du code qui crée un `BankAccount` :

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

Ensuite, testez l’interception des conditions d’erreur en essayant de créer un compte avec un solde négatif. Ajoutez le code suivant après le code précédent que vous venez d’ajouter :

```csharp
// Test that the initial balances must be positive.
try
{
    var invalidAccount = new BankAccount("invalid", -55);
}
catch (ArgumentOutOfRangeException e)
{
    Console.WriteLine("Exception caught creating account with negative balance");
    Console.WriteLine(e.ToString());
}
```

Vous utilisez les [ `try` `catch` instructions et](../../language-reference/keywords/try-catch.md) pour marquer un bloc de code qui peut lever des exceptions et intercepter les erreurs que vous attendez. Vous pouvez utiliser la même technique pour tester le code qui lève une exception pour un solde négatif. Ajoutez le code suivant à la fin de votre `Main` méthode :

```csharp
// Test for a negative balance.
try
{
    account.MakeWithdrawal(750, DateTime.Now, "Attempt to overdraw");
}
catch (InvalidOperationException e)
{
    Console.WriteLine("Exception caught trying to overdraw");
    Console.WriteLine(e.ToString());
}
```

Enregistrez le fichier et tapez `dotnet run` pour effectuer un essai.

## <a name="challenge---log-all-transactions"></a>Test : consigner toutes les transactions

Pour terminer ce tutoriel, vous pouvez écrire la méthode `GetAccountHistory` qui crée une `string` pour l’historique des transactions. Ajoutez cette méthode au type `BankAccount` :

[!code-csharp[History](~/samples/snippets/csharp/classes-quickstart/BankAccount.cs#History)]

Cette méthode utilise la classe <xref:System.Text.StringBuilder> pour mettre en forme une chaîne contenant une ligne par transaction. Vous avez vu le code de mise en forme de chaîne précédemment dans ces tutoriels. Vous pouvez observer le nouveau caractère `\t`. Celui-ci insère une tabulation pour mettre en forme la sortie.

Ajoutez cette ligne pour effectuer un essai dans *Program.cs* :

```csharp
Console.WriteLine(account.GetAccountHistory());
```

Exécutez votre programme pour voir les résultats.

## <a name="next-steps"></a>Étapes suivantes

Si vous vous êtes bloqué, vous pouvez voir la source de ce didacticiel [dans notre référentiel GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/classes-quickstart/).

Félicitations, vous avez terminé toute notre présentation des tutoriels C#. Si vous souhaitez en savoir plus, essayez d’autres [didacticiels](../index.md).
