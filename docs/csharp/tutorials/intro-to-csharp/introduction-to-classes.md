---
title: Classes et objets – Présentation du tutoriel C#
description: Créez votre premier programme C# et explorez les concepts orientés objet
ms.date: 10/11/2017
ms.custom: mvc
ms.openlocfilehash: 90abe3836292029ce7ebf26ae9be3253c4eface1
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756050"
---
# <a name="explore-object-oriented-programming-with-classes-and-objects"></a><span data-ttu-id="3429c-103">Explorez la programmation orientée objet avec des classes et des objets</span><span class="sxs-lookup"><span data-stu-id="3429c-103">Explore object oriented programming with classes and objects</span></span>

<span data-ttu-id="3429c-104">Ce tutoriel suppose que vous disposez d’un ordinateur que vous pouvez utiliser pour le développement.</span><span class="sxs-lookup"><span data-stu-id="3429c-104">This tutorial expects that you have a machine you can use for development.</span></span> <span data-ttu-id="3429c-105">Le didacticiel .NET [Hello World en 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) contient des instructions pour la configuration de votre environnement de développement local sur Windows, Linux ou MacOS.</span><span class="sxs-lookup"><span data-stu-id="3429c-105">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="3429c-106">Vous trouverez une brève vue d’ensemble des commandes utilisées dans [Se familiariser avec les outils de développement](local-environment.md), avec des liens vers des informations complémentaires.</span><span class="sxs-lookup"><span data-stu-id="3429c-106">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="create-your-application"></a><span data-ttu-id="3429c-107">Créer votre application</span><span class="sxs-lookup"><span data-stu-id="3429c-107">Create your application</span></span>

<span data-ttu-id="3429c-108">Dans une fenêtre de terminal, créez un répertoire nommé *classes*.</span><span class="sxs-lookup"><span data-stu-id="3429c-108">Using a terminal window, create a directory named *classes*.</span></span> <span data-ttu-id="3429c-109">Vous y créerez votre application.</span><span class="sxs-lookup"><span data-stu-id="3429c-109">You'll build your application there.</span></span> <span data-ttu-id="3429c-110">Sélectionnez ce répertoire et tapez `dotnet new console` dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="3429c-110">Change to that directory and type `dotnet new console` in the console window.</span></span> <span data-ttu-id="3429c-111">Cette commande crée votre application.</span><span class="sxs-lookup"><span data-stu-id="3429c-111">This command creates your application.</span></span> <span data-ttu-id="3429c-112">Ouvrez *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="3429c-112">Open *Program.cs*.</span></span> <span data-ttu-id="3429c-113">Il doit se présenter comme suit :</span><span class="sxs-lookup"><span data-stu-id="3429c-113">It should look like this:</span></span>

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

<span data-ttu-id="3429c-114">Dans ce tutoriel, vous allez créer des types qui représentent un compte bancaire.</span><span class="sxs-lookup"><span data-stu-id="3429c-114">In this tutorial, you're going to create new types that represent a bank account.</span></span> <span data-ttu-id="3429c-115">Les développeurs définissent généralement chaque classe dans un fichier texte différent.</span><span class="sxs-lookup"><span data-stu-id="3429c-115">Typically developers define each class in a different text file.</span></span> <span data-ttu-id="3429c-116">Cela simplifie la gestion au fur et à mesure qu’un programme augmente en taille.</span><span class="sxs-lookup"><span data-stu-id="3429c-116">That makes it easier to manage as a program grows in size.</span></span> <span data-ttu-id="3429c-117">Créez un fichier nommé *BankAccount.cs* dans le répertoire *classes*.</span><span class="sxs-lookup"><span data-stu-id="3429c-117">Create a new file named *BankAccount.cs* in the *classes* directory.</span></span>

<span data-ttu-id="3429c-118">Ce fichier contiendra la définition d’un ***compte bancaire***.</span><span class="sxs-lookup"><span data-stu-id="3429c-118">This file will contain the definition of a ***bank account***.</span></span> <span data-ttu-id="3429c-119">La programmation orientée objet organise le code en créant des types sous la forme de ***classes***.</span><span class="sxs-lookup"><span data-stu-id="3429c-119">Object Oriented programming organizes code by creating types in the form of ***classes***.</span></span> <span data-ttu-id="3429c-120">Ces classes contiennent le code qui représente une entité spécifique.</span><span class="sxs-lookup"><span data-stu-id="3429c-120">These classes contain the code that represents a specific entity.</span></span> <span data-ttu-id="3429c-121">La classe `BankAccount` représente un compte bancaire.</span><span class="sxs-lookup"><span data-stu-id="3429c-121">The `BankAccount` class represents a bank account.</span></span> <span data-ttu-id="3429c-122">Le code implémente des opérations spécifiques à travers des méthodes et des propriétés.</span><span class="sxs-lookup"><span data-stu-id="3429c-122">The code implements specific operations through methods and properties.</span></span> <span data-ttu-id="3429c-123">Dans ce tutoriel, le compte bancaire prend en charge le comportement suivant :</span><span class="sxs-lookup"><span data-stu-id="3429c-123">In this tutorial, the bank account supports this behavior:</span></span>

1. <span data-ttu-id="3429c-124">Il contient un numéro à 10 chiffres qui identifie le compte bancaire de manière unique.</span><span class="sxs-lookup"><span data-stu-id="3429c-124">It has a 10-digit number that uniquely identifies the bank account.</span></span>
1. <span data-ttu-id="3429c-125">Il contient une chaîne qui stocke le nom du ou des détenteurs.</span><span class="sxs-lookup"><span data-stu-id="3429c-125">It has a string that stores the name or names of the owners.</span></span>
1. <span data-ttu-id="3429c-126">Le solde peut être récupéré.</span><span class="sxs-lookup"><span data-stu-id="3429c-126">The balance can be retrieved.</span></span>
1. <span data-ttu-id="3429c-127">Il accepte les dépôts.</span><span class="sxs-lookup"><span data-stu-id="3429c-127">It accepts deposits.</span></span>
1. <span data-ttu-id="3429c-128">Il accepte les retraits.</span><span class="sxs-lookup"><span data-stu-id="3429c-128">It accepts withdrawals.</span></span>
1. <span data-ttu-id="3429c-129">Le solde initial doit être positif.</span><span class="sxs-lookup"><span data-stu-id="3429c-129">The initial balance must be positive.</span></span>
1. <span data-ttu-id="3429c-130">Les retraits ne peuvent pas générer un solde négatif.</span><span class="sxs-lookup"><span data-stu-id="3429c-130">Withdrawals cannot result in a negative balance.</span></span>

## <a name="define-the-bank-account-type"></a><span data-ttu-id="3429c-131">Définir le type de compte bancaire</span><span class="sxs-lookup"><span data-stu-id="3429c-131">Define the bank account type</span></span>

<span data-ttu-id="3429c-132">Vous pouvez commencer par créer les éléments de base d’une classe définissant ce comportement.</span><span class="sxs-lookup"><span data-stu-id="3429c-132">You can start by creating the basics of a class that defines that behavior.</span></span> <span data-ttu-id="3429c-133">Créez un nouveau fichier à l’aide de la commande **file : New** .</span><span class="sxs-lookup"><span data-stu-id="3429c-133">Create a new file using the **File:New** command.</span></span> <span data-ttu-id="3429c-134">Nommez-le *BankAccount.cs*.</span><span class="sxs-lookup"><span data-stu-id="3429c-134">Name it *BankAccount.cs*.</span></span> <span data-ttu-id="3429c-135">Ajoutez le code suivant à votre fichier *BankAccount.cs* :</span><span class="sxs-lookup"><span data-stu-id="3429c-135">Add the following code to your *BankAccount.cs* file:</span></span>

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

<span data-ttu-id="3429c-136">Avant de poursuivre, examinons ce que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="3429c-136">Before going on, let's take a look at what you've built.</span></span>  <span data-ttu-id="3429c-137">La déclaration `namespace` permet d’organiser logiquement votre code.</span><span class="sxs-lookup"><span data-stu-id="3429c-137">The `namespace` declaration provides a way to logically organize your code.</span></span> <span data-ttu-id="3429c-138">Ce tutoriel étant relativement petit, vous allez placer tout le code dans un même espace de noms.</span><span class="sxs-lookup"><span data-stu-id="3429c-138">This tutorial is relatively small, so you'll put all the code in one namespace.</span></span>

<span data-ttu-id="3429c-139">`public class BankAccount` définit la classe ou le type que vous créez.</span><span class="sxs-lookup"><span data-stu-id="3429c-139">`public class BankAccount` defines the class, or type, you are creating.</span></span> <span data-ttu-id="3429c-140">Tout ce qui se trouve à l’intérieur du `{` et `}` qui suit la déclaration de classe définit l’État et le comportement de la classe.</span><span class="sxs-lookup"><span data-stu-id="3429c-140">Everything inside the `{` and `}` that follows the class declaration defines the state and behavior of the class.</span></span> <span data-ttu-id="3429c-141">La classe `BankAccount` a cinq ***membres***.</span><span class="sxs-lookup"><span data-stu-id="3429c-141">There are five ***members*** of the `BankAccount` class.</span></span> <span data-ttu-id="3429c-142">Les trois premiers sont des ***propriétés***.</span><span class="sxs-lookup"><span data-stu-id="3429c-142">The first three are ***properties***.</span></span> <span data-ttu-id="3429c-143">Les propriétés sont des éléments de données qui peuvent avoir un code qui applique la validation ou d’autres règles.</span><span class="sxs-lookup"><span data-stu-id="3429c-143">Properties are data elements and can have code that enforces validation or other rules.</span></span> <span data-ttu-id="3429c-144">Les deux derniers sont des ***méthodes***.</span><span class="sxs-lookup"><span data-stu-id="3429c-144">The last two are ***methods***.</span></span> <span data-ttu-id="3429c-145">Les méthodes sont des blocs de code qui effectuent une fonction unique.</span><span class="sxs-lookup"><span data-stu-id="3429c-145">Methods are blocks of code that perform a single function.</span></span> <span data-ttu-id="3429c-146">La lecture des noms de chacun des membres doit fournir suffisamment d’informations pour vous permettre (ou à tout autre développeur) de comprendre ce que fait la classe.</span><span class="sxs-lookup"><span data-stu-id="3429c-146">Reading the names of each of the members should provide enough information for you or another developer to understand what the class does.</span></span>

## <a name="open-a-new-account"></a><span data-ttu-id="3429c-147">Ouvrir un nouveau compte</span><span class="sxs-lookup"><span data-stu-id="3429c-147">Open a new account</span></span>

<span data-ttu-id="3429c-148">La première fonctionnalité à implémenter est l’ouverture d’un compte bancaire.</span><span class="sxs-lookup"><span data-stu-id="3429c-148">The first feature to implement is to open a bank account.</span></span> <span data-ttu-id="3429c-149">Quand un client ouvre un compte, il doit fournir un solde initial, ainsi que des informations sur le ou les détenteurs du compte.</span><span class="sxs-lookup"><span data-stu-id="3429c-149">When a customer opens an account, they must supply an initial balance, and information about the owner or owners of that account.</span></span>

<span data-ttu-id="3429c-150">La création d’un objet du type `BankAccount` suppose la définition d’un ***constructeur*** qui assigne ces valeurs.</span><span class="sxs-lookup"><span data-stu-id="3429c-150">Creating a new object of the `BankAccount` type means defining a ***constructor*** that assigns those values.</span></span> <span data-ttu-id="3429c-151">Un ***constructeur*** est un membre qui porte le même nom que la classe.</span><span class="sxs-lookup"><span data-stu-id="3429c-151">A ***constructor*** is a member that has the same name as the class.</span></span> <span data-ttu-id="3429c-152">Il est utilisé pour initialiser des objets de ce type de classe.</span><span class="sxs-lookup"><span data-stu-id="3429c-152">It is used to initialize objects of that class type.</span></span> <span data-ttu-id="3429c-153">Ajoutez le constructeur suivant au `BankAccount` type.</span><span class="sxs-lookup"><span data-stu-id="3429c-153">Add the following constructor to the `BankAccount` type.</span></span> <span data-ttu-id="3429c-154">Placez le code suivant au-dessus de la déclaration de `MakeDeposit` :</span><span class="sxs-lookup"><span data-stu-id="3429c-154">Place the following code above the declaration of `MakeDeposit`:</span></span>

```csharp
public BankAccount(string name, decimal initialBalance)
{
    this.Owner = name;
    this.Balance = initialBalance;
}
```

<span data-ttu-id="3429c-155">Les constructeurs sont appelés lorsque vous créez un objet à l’aide de [`new`](../../language-reference/operators/new-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="3429c-155">Constructors are called when you create an object using [`new`](../../language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="3429c-156">Remplacez la ligne `Console.WriteLine("Hello World!");` dans *Program.cs* par le code suivant (remplacez `<name>` par votre nom) :</span><span class="sxs-lookup"><span data-stu-id="3429c-156">Replace the line `Console.WriteLine("Hello World!");` in *Program.cs* with the following code (replace `<name>` with your name):</span></span>

```csharp
var account = new BankAccount("<name>", 1000);
Console.WriteLine($"Account {account.Number} was created for {account.Owner} with {account.Balance} initial balance.");
```

<span data-ttu-id="3429c-157">Exécutons ce que vous avez créé jusqu’à présent.</span><span class="sxs-lookup"><span data-stu-id="3429c-157">Let's run what you've built so far.</span></span> <span data-ttu-id="3429c-158">Si vous utilisez Visual Studio, sélectionnez exécuter **sans débogage** dans le menu **exécuter** .</span><span class="sxs-lookup"><span data-stu-id="3429c-158">If you're using Visual Studio, Select **Start without debugging** from the **Run** menu.</span></span> <span data-ttu-id="3429c-159">Si vous utilisez une ligne de commande, tapez `dotnet run` le répertoire dans lequel vous avez créé votre projet.</span><span class="sxs-lookup"><span data-stu-id="3429c-159">If you're using a command line, type `dotnet run` in the directory where you've created your project.</span></span>

<span data-ttu-id="3429c-160">Avez-vous remarqué que le numéro de compte est vide ?</span><span class="sxs-lookup"><span data-stu-id="3429c-160">Did you notice that the account number is blank?</span></span> <span data-ttu-id="3429c-161">L’heure est venue de traiter ce point.</span><span class="sxs-lookup"><span data-stu-id="3429c-161">It's time to fix that.</span></span> <span data-ttu-id="3429c-162">Le numéro de compte doit être assigné une fois l’objet construit.</span><span class="sxs-lookup"><span data-stu-id="3429c-162">The account number should be assigned when the object is constructed.</span></span> <span data-ttu-id="3429c-163">Mais ce ne devrait pas être à l’appelant de le créer.</span><span class="sxs-lookup"><span data-stu-id="3429c-163">But it shouldn't be the responsibility of the caller to create it.</span></span> <span data-ttu-id="3429c-164">Le code de la classe `BankAccount` devrait savoir comment assigner de nouveaux numéros de compte.</span><span class="sxs-lookup"><span data-stu-id="3429c-164">The `BankAccount` class code should know how to assign new account numbers.</span></span>  <span data-ttu-id="3429c-165">Un moyen simple de le faire consiste à commencer par un numéro à 10 chiffres.</span><span class="sxs-lookup"><span data-stu-id="3429c-165">A simple way to do this is to start with a 10-digit number.</span></span> <span data-ttu-id="3429c-166">Incrémentez-le chaque fois qu’un compte est créé.</span><span class="sxs-lookup"><span data-stu-id="3429c-166">Increment it when each new account is created.</span></span> <span data-ttu-id="3429c-167">Enfin, stockez le numéro de compte actuel quand un objet est construit.</span><span class="sxs-lookup"><span data-stu-id="3429c-167">Finally, store the current account number when an object is constructed.</span></span>

<span data-ttu-id="3429c-168">Ajoutez une déclaration de membre à la `BankAccount` classe.</span><span class="sxs-lookup"><span data-stu-id="3429c-168">Add a member declaration to the `BankAccount` class.</span></span> <span data-ttu-id="3429c-169">Placez la ligne de code suivante après l’accolade ouvrante `{` au début de la `BankAccount` classe :</span><span class="sxs-lookup"><span data-stu-id="3429c-169">Place the following line of code after the opening brace `{` at the beginning of the `BankAccount` class:</span></span>

```csharp
private static int accountNumberSeed = 1234567890;
```

<span data-ttu-id="3429c-170">Il s’agit d’un membre de données.</span><span class="sxs-lookup"><span data-stu-id="3429c-170">This is a data member.</span></span> <span data-ttu-id="3429c-171">Celui-ci est `private`, ce qui signifie qu’il est uniquement accessible par code dans la classe `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="3429c-171">It's `private`, which means it can only be accessed by code inside the `BankAccount` class.</span></span> <span data-ttu-id="3429c-172">C’est un moyen de séparer les responsabilités publiques (comme la présence d’un numéro de compte) de l’implémentation privée (comment les numéros de compte sont générés).</span><span class="sxs-lookup"><span data-stu-id="3429c-172">It's a way of separating the public responsibilities (like having an account number) from the private implementation (how account numbers are generated).</span></span> <span data-ttu-id="3429c-173">Il est également `static`, ce qui signifie qu’il est partagé par toutes les objets `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="3429c-173">It is also `static`, which means it is shared by all of the `BankAccount` objects.</span></span> <span data-ttu-id="3429c-174">La valeur d’une variable non statique est unique pour chaque instance de l’objet `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="3429c-174">The value of a non-static variable is unique to each instance of the `BankAccount` object.</span></span> <span data-ttu-id="3429c-175">Ajoutez les deux lignes suivantes au constructeur pour assigner le numéro de compte.</span><span class="sxs-lookup"><span data-stu-id="3429c-175">Add the following two lines to the constructor to assign the account number.</span></span> <span data-ttu-id="3429c-176">Placez-les après la ligne qui indique `this.Balance = initialBalance` :</span><span class="sxs-lookup"><span data-stu-id="3429c-176">Place them after the line that says `this.Balance = initialBalance`:</span></span>

```csharp
this.Number = accountNumberSeed.ToString();
accountNumberSeed++;
```

<span data-ttu-id="3429c-177">Tapez `dotnet run` pour afficher les résultats.</span><span class="sxs-lookup"><span data-stu-id="3429c-177">Type `dotnet run` to see the results.</span></span>

## <a name="create-deposits-and-withdrawals"></a><span data-ttu-id="3429c-178">Créer des dépôts et des retraits</span><span class="sxs-lookup"><span data-stu-id="3429c-178">Create deposits and withdrawals</span></span>

<span data-ttu-id="3429c-179">La classe de votre compte bancaire doit accepter les dépôts et les retraits pour fonctionner correctement.</span><span class="sxs-lookup"><span data-stu-id="3429c-179">Your bank account class needs to accept deposits and withdrawals to work correctly.</span></span> <span data-ttu-id="3429c-180">Nous allons implémenter des dépôts et des retraits en créant un journal de chaque transaction du compte.</span><span class="sxs-lookup"><span data-stu-id="3429c-180">Let's implement deposits and withdrawals by creating a journal of every transaction for the account.</span></span> <span data-ttu-id="3429c-181">Ce dernier présente plusieurs avantages par rapport à la simple mise à jour du solde à chaque transaction.</span><span class="sxs-lookup"><span data-stu-id="3429c-181">That has a few advantages over simply updating the balance on each transaction.</span></span> <span data-ttu-id="3429c-182">L’historique peut être utilisé pour auditer toutes les transactions et gérer les soldes au quotidien.</span><span class="sxs-lookup"><span data-stu-id="3429c-182">The history can be used to audit all transactions and manage daily balances.</span></span> <span data-ttu-id="3429c-183">En calculant le solde à partir de l’historique de toutes les transactions lorsque nécessaire, toutes les erreurs d’une même transaction qui sont résolues apparaîtront correctement dans le solde dans le calcul suivant.</span><span class="sxs-lookup"><span data-stu-id="3429c-183">By computing the balance from the history of all transactions when needed, any errors in a single transaction that are fixed will be correctly reflected in the balance on the next computation.</span></span>

<span data-ttu-id="3429c-184">Commençons par créer un type pour représenter une transaction.</span><span class="sxs-lookup"><span data-stu-id="3429c-184">Let's start by creating a new type to represent a transaction.</span></span> <span data-ttu-id="3429c-185">Il s’agit d’un type simple qui n’a aucune responsabilité.</span><span class="sxs-lookup"><span data-stu-id="3429c-185">This is a simple type that doesn't have any responsibilities.</span></span> <span data-ttu-id="3429c-186">Il a besoin de quelques propriétés.</span><span class="sxs-lookup"><span data-stu-id="3429c-186">It needs a few properties.</span></span> <span data-ttu-id="3429c-187">Créez un fichier nommé *Transaction.cs*.</span><span class="sxs-lookup"><span data-stu-id="3429c-187">Create a new file named *Transaction.cs*.</span></span> <span data-ttu-id="3429c-188">Ajoutez-lui le code suivant :</span><span class="sxs-lookup"><span data-stu-id="3429c-188">Add the following code to it:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/Transaction.cs":::

<span data-ttu-id="3429c-189">Nous allons maintenant ajouter une <xref:System.Collections.Generic.List%601> d’objets `Transaction` à la classe `BankAccount`.</span><span class="sxs-lookup"><span data-stu-id="3429c-189">Now, let's add a <xref:System.Collections.Generic.List%601> of `Transaction` objects to the `BankAccount` class.</span></span> <span data-ttu-id="3429c-190">Ajoutez la déclaration suivante après le constructeur dans votre fichier *BankAccount.cs* :</span><span class="sxs-lookup"><span data-stu-id="3429c-190">Add the following declaration after the constructor in your *BankAccount.cs* file:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="TransactionDeclaration":::

<span data-ttu-id="3429c-191">Avec la classe <xref:System.Collections.Generic.List%601>, vous devez importer un espace de noms différent.</span><span class="sxs-lookup"><span data-stu-id="3429c-191">The <xref:System.Collections.Generic.List%601> class requires you to import a different namespace.</span></span> <span data-ttu-id="3429c-192">Ajoutez le code suivant au début de *BankAccount.cs* :</span><span class="sxs-lookup"><span data-stu-id="3429c-192">Add the following at the beginning of *BankAccount.cs*:</span></span>

```csharp
using System.Collections.Generic;
```

<span data-ttu-id="3429c-193">Nous allons à présent modifier la façon dont le `Balance` est présenté.</span><span class="sxs-lookup"><span data-stu-id="3429c-193">Now, let's change how the `Balance` is reported.</span></span>  <span data-ttu-id="3429c-194">Il peut être obtenu en additionnant les valeurs de toutes les transactions.</span><span class="sxs-lookup"><span data-stu-id="3429c-194">It can be found by summing the values of all transactions.</span></span> <span data-ttu-id="3429c-195">Modifiez la déclaration de `Balance` dans la classe `BankAccount` comme suit :</span><span class="sxs-lookup"><span data-stu-id="3429c-195">Modify the declaration of `Balance` in the `BankAccount` class to the following:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="BalanceComputation":::

<span data-ttu-id="3429c-196">Cet exemple montre un aspect important des ***propriétés***.</span><span class="sxs-lookup"><span data-stu-id="3429c-196">This example shows an important aspect of ***properties***.</span></span> <span data-ttu-id="3429c-197">Vous calculez à présent le solde quand un autre programmeur en demande la valeur.</span><span class="sxs-lookup"><span data-stu-id="3429c-197">You're now computing the balance when another programmer asks for the value.</span></span> <span data-ttu-id="3429c-198">Votre calcul énumère toutes les transactions et retourne la somme en tant que solde actuel.</span><span class="sxs-lookup"><span data-stu-id="3429c-198">Your computation enumerates all transactions, and provides the sum as the current balance.</span></span>

<span data-ttu-id="3429c-199">Implémentez ensuite les méthodes `MakeDeposit` et `MakeWithdrawal`.</span><span class="sxs-lookup"><span data-stu-id="3429c-199">Next, implement the `MakeDeposit` and `MakeWithdrawal` methods.</span></span> <span data-ttu-id="3429c-200">Ces méthodes appliquent les deux règles finales suivantes : le solde initial doit être positif et un retrait ne doit pas générer de solde négatif.</span><span class="sxs-lookup"><span data-stu-id="3429c-200">These methods will enforce the final two rules: that the initial balance must be positive, and that any withdrawal must not create a negative balance.</span></span>

<span data-ttu-id="3429c-201">Cela introduit le concept d’***exceptions***.</span><span class="sxs-lookup"><span data-stu-id="3429c-201">This introduces the concept of ***exceptions***.</span></span> <span data-ttu-id="3429c-202">Le moyen typique d’indiquer qu’une méthode ne peut pas effectuer correctement son travail consiste à lever une exception.</span><span class="sxs-lookup"><span data-stu-id="3429c-202">The standard way of indicating that a method cannot complete its work successfully is to throw an exception.</span></span> <span data-ttu-id="3429c-203">Le type d’exception et le message associé décrivent l’erreur.</span><span class="sxs-lookup"><span data-stu-id="3429c-203">The type of exception and the message associated with it describe the error.</span></span> <span data-ttu-id="3429c-204">Ici, la méthode `MakeDeposit` lève une exception si le montant du dépôt est négatif.</span><span class="sxs-lookup"><span data-stu-id="3429c-204">Here, the `MakeDeposit` method throws an exception if the amount of the deposit is negative.</span></span> <span data-ttu-id="3429c-205">La `MakeWithdrawal` méthode lève une exception si le montant du retrait est négatif ou si l’application du retrait entraîne un solde négatif.</span><span class="sxs-lookup"><span data-stu-id="3429c-205">The `MakeWithdrawal` method throws an exception if the withdrawal amount is negative, or if applying the withdrawal results in a negative balance.</span></span> <span data-ttu-id="3429c-206">Ajoutez le code suivant après la déclaration de la `allTransactions` liste :</span><span class="sxs-lookup"><span data-stu-id="3429c-206">Add the following code after the declaration of the `allTransactions` list:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="DepositAndWithdrawal":::

<span data-ttu-id="3429c-207">L' [`throw`](../../language-reference/keywords/throw.md) instruction **lève** une exception.</span><span class="sxs-lookup"><span data-stu-id="3429c-207">The [`throw`](../../language-reference/keywords/throw.md) statement **throws** an exception.</span></span> <span data-ttu-id="3429c-208">L’exécution du bloc actuel se termine et le contrôle est transféré au premier bloc correspondant `catch` trouvé dans la pile des appels.</span><span class="sxs-lookup"><span data-stu-id="3429c-208">Execution of the current block ends, and control transfers to the first matching `catch` block found in the call stack.</span></span> <span data-ttu-id="3429c-209">Vous ajouterez un bloc `catch` pour tester ce code un peu plus tard.</span><span class="sxs-lookup"><span data-stu-id="3429c-209">You'll add a `catch` block to test this code a little later on.</span></span>

<span data-ttu-id="3429c-210">Le constructeur devrait obtenir une modification lui permettant d’ajouter une transaction initiale au lieu de mettre directement le solde à jour.</span><span class="sxs-lookup"><span data-stu-id="3429c-210">The constructor should get one change so that it adds an initial transaction, rather than updating the balance directly.</span></span> <span data-ttu-id="3429c-211">Étant donné que vous avez déjà écrit la méthode `MakeDeposit`, appelez-la à partir de votre constructeur.</span><span class="sxs-lookup"><span data-stu-id="3429c-211">Since you already wrote the `MakeDeposit` method, call it from your constructor.</span></span> <span data-ttu-id="3429c-212">Le constructeur terminé doit être semblable à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="3429c-212">The finished constructor should look like this:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="Constructor":::

<span data-ttu-id="3429c-213"><xref:System.DateTime.Now?displayProperty=nameWithType> est une propriété qui retourne la date et l'heure actuelles.</span><span class="sxs-lookup"><span data-stu-id="3429c-213"><xref:System.DateTime.Now?displayProperty=nameWithType> is a property that returns the current date and time.</span></span> <span data-ttu-id="3429c-214">Pour tester cela, ajoutez quelques dépôts et retraits dans votre `Main` méthode, à la suite du code qui crée un `BankAccount` :</span><span class="sxs-lookup"><span data-stu-id="3429c-214">Test this by adding a few deposits and withdrawals in your `Main` method, following the code that creates a new `BankAccount`:</span></span>

```csharp
account.MakeWithdrawal(500, DateTime.Now, "Rent payment");
Console.WriteLine(account.Balance);
account.MakeDeposit(100, DateTime.Now, "Friend paid me back");
Console.WriteLine(account.Balance);
```

<span data-ttu-id="3429c-215">Ensuite, testez l’interception des conditions d’erreur en essayant de créer un compte avec un solde négatif.</span><span class="sxs-lookup"><span data-stu-id="3429c-215">Next, test that you are catching error conditions by trying to create an account with a negative balance.</span></span> <span data-ttu-id="3429c-216">Ajoutez le code suivant après le code précédent que vous venez d’ajouter :</span><span class="sxs-lookup"><span data-stu-id="3429c-216">Add the following code after the preceding code you just added:</span></span>

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

<span data-ttu-id="3429c-217">Vous utilisez les [ `try` `catch` instructions et](../../language-reference/keywords/try-catch.md) pour marquer un bloc de code qui peut lever des exceptions et intercepter les erreurs que vous attendez.</span><span class="sxs-lookup"><span data-stu-id="3429c-217">You use the [`try` and `catch` statements](../../language-reference/keywords/try-catch.md) to mark a block of code that may throw exceptions and to catch those errors that you expect.</span></span> <span data-ttu-id="3429c-218">Vous pouvez utiliser la même technique pour tester le code qui lève une exception pour un solde négatif.</span><span class="sxs-lookup"><span data-stu-id="3429c-218">You can use the same technique to test the code that throws an exception for a negative balance.</span></span> <span data-ttu-id="3429c-219">Ajoutez le code suivant à la fin de votre `Main` méthode :</span><span class="sxs-lookup"><span data-stu-id="3429c-219">Add the following code at the end of your `Main` method:</span></span>

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

<span data-ttu-id="3429c-220">Enregistrez le fichier et tapez `dotnet run` pour effectuer un essai.</span><span class="sxs-lookup"><span data-stu-id="3429c-220">Save the file and type `dotnet run` to try it.</span></span>

## <a name="challenge---log-all-transactions"></a><span data-ttu-id="3429c-221">Test : consigner toutes les transactions</span><span class="sxs-lookup"><span data-stu-id="3429c-221">Challenge - log all transactions</span></span>

<span data-ttu-id="3429c-222">Pour terminer ce tutoriel, vous pouvez écrire la méthode `GetAccountHistory` qui crée une `string` pour l’historique des transactions.</span><span class="sxs-lookup"><span data-stu-id="3429c-222">To finish this tutorial, you can write the `GetAccountHistory` method that creates a `string` for the transaction history.</span></span> <span data-ttu-id="3429c-223">Ajoutez cette méthode au type `BankAccount` :</span><span class="sxs-lookup"><span data-stu-id="3429c-223">Add this method to the `BankAccount` type:</span></span>

:::code language="csharp" source="./snippets/introduction-to-classes/BankAccount.cs" id="History":::

<span data-ttu-id="3429c-224">Cette méthode utilise la classe <xref:System.Text.StringBuilder> pour mettre en forme une chaîne contenant une ligne par transaction.</span><span class="sxs-lookup"><span data-stu-id="3429c-224">This uses the <xref:System.Text.StringBuilder> class to format a string that contains one line for each transaction.</span></span> <span data-ttu-id="3429c-225">Vous avez vu le code de mise en forme de chaîne précédemment dans ces tutoriels.</span><span class="sxs-lookup"><span data-stu-id="3429c-225">You've seen the string formatting code earlier in these tutorials.</span></span> <span data-ttu-id="3429c-226">Vous pouvez observer le nouveau caractère `\t`.</span><span class="sxs-lookup"><span data-stu-id="3429c-226">One new character is `\t`.</span></span> <span data-ttu-id="3429c-227">Celui-ci insère une tabulation pour mettre en forme la sortie.</span><span class="sxs-lookup"><span data-stu-id="3429c-227">That inserts a tab to format the output.</span></span>

<span data-ttu-id="3429c-228">Ajoutez cette ligne pour effectuer un essai dans *Program.cs* :</span><span class="sxs-lookup"><span data-stu-id="3429c-228">Add this line to test it in *Program.cs*:</span></span>

```csharp
Console.WriteLine(account.GetAccountHistory());
```

<span data-ttu-id="3429c-229">Exécutez votre programme pour voir les résultats.</span><span class="sxs-lookup"><span data-stu-id="3429c-229">Run your program to see the results.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3429c-230">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="3429c-230">Next steps</span></span>

<span data-ttu-id="3429c-231">Si vous vous êtes bloqué, vous pouvez voir la source de ce didacticiel [dans notre référentiel GitHub](https://github.com/dotnet/docs/tree/master/docs/csharp/tutorials/intro-to-csharp/snippets/introduction-to-classes).</span><span class="sxs-lookup"><span data-stu-id="3429c-231">If you got stuck, you can see the source for this tutorial [in our GitHub repo](https://github.com/dotnet/docs/tree/master/docs/csharp/tutorials/intro-to-csharp/snippets/introduction-to-classes).</span></span>

<span data-ttu-id="3429c-232">Vous pouvez poursuivre le didacticiel sur la [programmation orientée objet](object-oriented-programming.md) .</span><span class="sxs-lookup"><span data-stu-id="3429c-232">You can continue with the [object oriented programming](object-oriented-programming.md) tutorial.</span></span>

<span data-ttu-id="3429c-233">Pour plus d’informations sur ces concepts, consultez les articles suivants :</span><span class="sxs-lookup"><span data-stu-id="3429c-233">You can learn more about these concepts in these articles:</span></span>

- [<span data-ttu-id="3429c-234">Instruction if et else</span><span class="sxs-lookup"><span data-stu-id="3429c-234">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="3429c-235">While (instruction)</span><span class="sxs-lookup"><span data-stu-id="3429c-235">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="3429c-236">Instruction do</span><span class="sxs-lookup"><span data-stu-id="3429c-236">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="3429c-237">Instruction for</span><span class="sxs-lookup"><span data-stu-id="3429c-237">For statement</span></span>](../../language-reference/keywords/for.md)
