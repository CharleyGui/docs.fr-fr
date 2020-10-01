---
title: Programmation orientée objet (C#)
description: C# fournit une prise en charge complète de la programmation orientée objet, notamment l’abstraction, l’encapsulation, l’héritage et le polymorphisme.
ms.date: 09/30/2020
ms.openlocfilehash: 8a8dc8dc6d40c539b988ea203654d994e88c357a
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91614795"
---
# <a name="object-oriented-programming-c"></a>Programmation orientée objet (C#)

C# est un langage orienté objet. Quatre des techniques clés utilisées dans la programmation orientée objet sont les suivantes :

- L' *abstraction* signifie masquer les détails inutiles des consommateurs de type.
- L’*encapsulation* signifie qu’un groupe de propriétés, méthodes et autres membres corrélés est traité comme une unité ou un objet unique.
- L’*héritage* décrit la possibilité de créer des classes à partir d’une classe existante.
- Le *polymorphisme* signifie que plusieurs classes peuvent être utilisées de manière interchangeable, même si chacune des classes implémente les mêmes propriétés ou méthodes de manière différente.

Dans le didacticiel précédent, [Introduction aux classes](introduction-to-classes.md) , vous avez vu l' *abstraction* et l' *encapsulation*. La `BankAccount` classe a fourni une abstraction pour le concept d’un compte bancaire. Vous pouvez modifier son implémentation sans affecter le code qui a utilisé la `BankAccount` classe. Les `BankAccount` classes et `Transaction` fournissent toutes deux l’encapsulation des composants nécessaires à la description de ces concepts dans le code.

Dans ce didacticiel, vous allez étendre cette application pour utiliser *l’héritage* et le *polymorphisme* pour ajouter de nouvelles fonctionnalités. Vous ajouterez également des fonctionnalités à la `BankAccount` classe, en tirant parti des techniques d' *abstraction* et d' *encapsulation* que vous avez apprises dans le didacticiel précédent.

## <a name="create-different-types-of-accounts"></a>Créer différents types de comptes

Une fois ce programme créé, vous recevez des demandes d’ajout de fonctionnalités. Il fonctionne très bien dans le cas où il n’existe qu’un seul type de compte bancaire. Au fil du temps, des besoins changent et des types de compte associés sont demandés :

- Un compte d’intérêt qui accumule des intérêts à la fin de chaque mois.
- Une ligne de crédit qui peut avoir un solde négatif, mais lorsqu’il y a un solde, des frais sont facturés chaque mois.
- Un compte de carte cadeau prépayé qui commence par un dépôt unique et qui ne peut être payé. Il peut être rerempli une fois au début de chaque mois.

Tous ces comptes différents sont similaires à ceux de `BankAccount` la classe définie dans le didacticiel précédent. Vous pouvez copier ce code, renommer les classes et apporter des modifications. Cette technique peut fonctionner à long terme, mais elle serait plus de travail au fil du temps. Toutes les modifications sont copiées dans toutes les classes affectées.

Au lieu de cela, vous pouvez créer des types de comptes bancaires qui héritent des méthodes et des données de la `BankAccount` classe créée dans le didacticiel précédent. Ces nouvelles classes peuvent étendre la `BankAccount` classe avec le comportement spécifique requis pour chaque type :

```csharp
public class InterestEarningAccount : BankAccount
{
}

public class LineOfCreditAccount : BankAccount
{
}

public class GiftCardAccount : BankAccount
{
}
```

Chacune de ces classes *hérite* du comportement partagé de sa *classe de base*partagée, la `BankAccount` classe. Écrivez les implémentations pour les fonctionnalités nouvelles et différentes dans chacune des *classes dérivées*.  Ces classes dérivées ont déjà tout le comportement défini dans la `BankAccount` classe.

Il est recommandé de créer chaque nouvelle classe dans un fichier source différent. Dans [Visual Studio](https://visualstudio.com), vous pouvez cliquer avec le bouton droit sur le projet, puis sélectionner *Ajouter une classe* pour ajouter une nouvelle classe dans un nouveau fichier. Dans [Visual Studio code](https://code.visualstudio.com), sélectionnez *fichier* , puis *nouveau* pour créer un nouveau fichier source. Dans l’un ou l’autre des outils, nommez le fichier pour qu’il corresponde à la classe : *InterestEarningAccount.cs*, *LineOfCreditAccount.cs*et *GiftCardAccount.cs*.

Lorsque vous créez les classes comme indiqué dans l’exemple précédent, vous découvrirez qu’aucune de vos classes dérivées n’est compilée. Un constructeur est chargé d’initialiser un objet. Un constructeur de classe dérivée doit initialiser la classe dérivée et fournir des instructions sur la façon d’initialiser l’objet de classe de base inclus dans la classe dérivée. L’initialisation appropriée se produit normalement sans code supplémentaire. La `BankAccount` classe déclare un constructeur public avec la signature suivante :

```csharp
public BankAccount(string name, decimal initialBalance)
```

Le compilateur ne génère pas de constructeur par défaut lorsque vous définissez un constructeur vous-même. Cela signifie que chaque classe dérivée doit appeler explicitement ce constructeur. Vous déclarez un constructeur qui peut passer des arguments au constructeur de classe de base.  Le code suivant illustre le constructeur pour `InterestEarningAccount` :

:::code language="csharp" source="./snippets/object-oriented-programming/InterestEarningAccount.cs" ID="DerivedConstructor":::

Les paramètres de ce nouveau constructeur correspondent au type de paramètre et aux noms du constructeur de classe de base. Vous utilisez la `: base()` syntaxe pour indiquer un appel à un constructeur de classe de base. Certaines classes définissent plusieurs constructeurs, et cette syntaxe vous permet de choisir le constructeur de classe de base que vous appelez. Une fois que vous avez mis à jour les constructeurs, vous pouvez développer le code de chacune des classes dérivées. La configuration requise pour les nouvelles classes peut être indiquée comme suit :

- Compte de bénéfices intéressants :
  - Obtient un crédit de 2% du solde de fin de mois.
- Une ligne de crédit :
  - Peut avoir un solde négatif, mais pas une valeur absolue supérieure à la limite de crédit.
  - Entraînera un montant de frais pour les intérêts chaque mois où le solde de fin de mois n’est pas égal à 0.
  - Est facturé pour chaque retrait qui dépasse la limite de crédit.
- Un compte de carte cadeau :
  - Peut être rerempli avec un montant spécifié une fois par mois, le dernier jour du mois.

Vous pouvez voir que ces trois types de compte ont une action qui a lieu à la fin de chaque mois. Toutefois, chaque type de compte effectue des tâches différentes. Vous utilisez le *polymorphisme* pour implémenter ce code. Créez une `virtual` méthode unique dans la `BankAccount` classe :

:::code language="csharp" source="./snippets/object-oriented-programming/BankAccount.cs" ID="DeclareMonthEndTransactions":::

Le code précédent montre comment utiliser le `virtual` mot clé pour déclarer une méthode dans la classe de base qu’une classe dérivée peut fournir une implémentation différente pour. Une `virtual` méthode est une méthode dans laquelle toute classe dérivée peut choisir de réimplémenter. Les classes dérivées utilisent le `override` mot clé pour définir la nouvelle implémentation. En général, vous faites référence à ceci comme « substitution de l’implémentation de la classe de base ». Le `virtual` mot clé spécifie que les classes dérivées peuvent substituer le comportement. Vous pouvez également déclarer `abstract` des méthodes dans lesquelles les classes dérivées doivent remplacer le comportement. La classe de base ne fournit pas d’implémentation pour une `abstract` méthode. Ensuite, vous devez définir l’implémentation de deux des nouvelles classes que vous avez créées. Commencez par le `InterestEarningAccount` :

:::code language="csharp" source="./snippets/object-oriented-programming/InterestEarningAccount.cs" ID="ApplyMonthendInterest":::

Ajoutez le code suivant au `LineOfCreditAccount` . Le code inverse le solde pour calculer un montant positif qui est retiré du compte :

:::code language="csharp" source="./snippets/object-oriented-programming/LineOfCreditAccount.cs" ID="ApplyMonthendInterest":::

La `GiftCardAccount` classe a besoin de deux modifications pour implémenter ses fonctionnalités de fin de mois. Tout d’abord, modifiez le constructeur pour inclure une quantité facultative à ajouter chaque mois :

:::code language="csharp" source="./snippets/object-oriented-programming/GiftCardAccount.cs" ID="GiftCardAccountConstruction":::

Le constructeur fournit une valeur par défaut pour la `monthlyDeposit` valeur. ainsi, les appelants peuvent omettre un `0` pour aucun dépôt mensuel. Ensuite, remplacez la `PerformMonthEndTransactions` méthode pour ajouter le dépôt mensuel, s’il a été défini sur une valeur différente de zéro dans le constructeur :

:::code language="csharp" source="./snippets/object-oriented-programming/GiftCardAccount.cs" ID="AddMonthlyDeposit":::

Le remplacement applique l’ensemble de dépôts mensuels dans le constructeur. Ajoutez le code suivant à la `Main` méthode pour tester ces modifications pour le `GiftCardAccount` et le `InterestEarningAccount` :

:::code language="csharp" source="./snippets/object-oriented-programming/Program.cs" ID="FirstTests":::

Vérifiez les résultats. Ajoutez maintenant un ensemble similaire de code de test pour le `LineOfCreditAccount` :

:::code language="csharp" source="./snippets/object-oriented-programming/Program.cs" ID="TestLineOfCredit":::

Lorsque vous ajoutez le code précédent et exécutez le programme, un message semblable à l’erreur suivante s’affiche :

```console
Unhandled exception. System.ArgumentOutOfRangeException: Amount of deposit must be positive (Parameter 'amount')
   at OOProgramming.BankAccount.MakeDeposit(Decimal amount, DateTime date, String note) in BankAccount.cs:line 42
   at OOProgramming.BankAccount..ctor(String name, Decimal initialBalance) in BankAccount.cs:line 31
   at OOProgramming.LineOfCreditAccount..ctor(String name, Decimal initialBalance) in LineOfCreditAccount.cs:line 9
   at OOProgramming.Program.Main(String[] args) in Program.cs:line 29
```

> [!NOTE]
> La sortie réelle comprend le chemin d’accès complet au dossier contenant le projet. Les noms de dossiers ont été omis par souci de concision. En outre, selon le format de votre code, les numéros de ligne peuvent être légèrement différents.

Ce code échoue car le `BankAccount` suppose que le solde initial doit être supérieur à 0. Une autre hypothèse intégrée à la `BankAccount` classe est que le solde ne peut pas être négatif. Au lieu de cela, tout retrait qui dédessine le compte est rejeté. Ces deux hypothèses doivent être modifiées. Le compte de la ligne de crédit commence à 0 et est généralement un solde négatif. En outre, si un client emprunte trop d’argent, il est facturé. La transaction est acceptée, mais elle coûte juste plus cher. La première règle peut être implémentée en ajoutant un argument facultatif au `BankAccount` constructeur qui spécifie le solde minimal. La valeur par défaut est `0`. La deuxième règle requiert un mécanisme qui permet aux classes dérivées de modifier l’algorithme par défaut. Dans un sens, la classe de base « demande » le type dérivé qui doit se produire lorsqu’il y a un surplus. Le comportement par défaut consiste à rejeter la transaction en levant une exception.

Commençons par ajouter un deuxième constructeur qui comprend un paramètre facultatif `minimumBalance` . Ce nouveau constructeur effectue toutes les actions effectuées par le constructeur existant. En outre, il définit la propriété solde minimal. Vous pouvez copier le corps du constructeur existant. mais cela signifie que deux emplacements doivent être modifiés à l’avenir. Au lieu de cela, vous pouvez utiliser le *chaînage de constructeur* pour qu’un constructeur en appelle un autre. Le code suivant montre les deux constructeurs et le nouveau champ supplémentaire :

 :::code language="csharp" source="./snippets/object-oriented-programming/BankAccount.cs" ID="ConstructorModifications":::

Le code précédent illustre deux nouvelles techniques. Tout d’abord, le `minimumBalance` champ est marqué comme `readonly` . Cela signifie que la valeur ne peut pas être modifiée après la construction de l’objet. Une fois `BankAccount` créé, le `minimumBalance` ne peut pas changer. Deuxièmement, le constructeur qui accepte deux paramètres utilise `: this(name, initialBalance, 0) { }` comme implémentation. L' `: this()` expression appelle l’autre constructeur, celle avec trois paramètres. Cette technique vous permet d’avoir une seule implémentation pour l’initialisation d’un objet même si le code client peut choisir l’un des nombreux constructeurs.

Cette implémentation appelle `MakeDeposit` uniquement si le solde initial est supérieur à `0` . Cela préserve la règle selon laquelle les dépôts doivent être positifs, tout en permettant au compte de crédit de s’ouvrir avec un `0` solde.

Maintenant que la `BankAccount` classe a un champ en lecture seule pour le solde minimal, la modification finale consiste à remplacer le code en dur par `0` `minimumBalance` dans la `MakeWithdrawal` méthode :

```csharp
if (Balance - amount < minimumBalance)
```

Après l’extension de la `BankAccount` classe, vous pouvez modifier le `LineOfCreditAccount` constructeur pour appeler le nouveau constructeur de base, comme indiqué dans le code suivant :

:::code language="csharp" source="./snippets/object-oriented-programming/LineOfCreditAccount.cs" ID="ConstructLineOfCredit":::

Notez que le `LineOfCreditAccount` constructeur modifie le signe du `creditLimit` paramètre afin qu’il corresponde à la signification du `minimumBalance` paramètre.

## <a name="different-overdraft-rules"></a>Autres règles de prébrouillon

La dernière fonctionnalité à ajouter permet au `LineOfCreditAccount` de payer une taxe pour dépasser la limite de crédit au lieu de refuser la transaction.

Une technique consiste à définir une fonction virtuelle où vous implémentez le comportement requis. La `Bank Account` classe refactorise la `MakeWithdrawal` méthode en deux méthodes. La nouvelle méthode effectue l’action spécifiée lorsque le retrait prend le solde inférieur au minimum. La `MakeWithdrawal` méthode existante a le code suivant :

```csharp
public void MakeWithdrawal(decimal amount, DateTime date, string note)
{
    if (amount <= 0)
    {
        throw new ArgumentOutOfRangeException(nameof(amount), "Amount of withdrawal must be positive");
    }
    if (Balance - amount < minimumBalance)
    {
        throw new InvalidOperationException("Not sufficient funds for this withdrawal");
    }
    var withdrawal = new Transaction(-amount, date, note);
    allTransactions.Add(withdrawal);
}
```

Remplacez-le par le code suivant :

:::code language="csharp" source="./snippets/object-oriented-programming/BankAccount.cs" ID="RefactoredMakeWithdrawal":::

La méthode ajoutée est, ce qui signifie qu’elle ne peut être appelée qu’à partir de classes dérivées. Cette déclaration empêche d’autres clients d’appeler la méthode. Cela permet également `virtual` aux classes dérivées de modifier le comportement. Le type de retour est `Transaction?` . L' `?` annotation indique que la méthode peut retourner `null` . Ajoutez l’implémentation suivante dans le `LineOfCreditAccount` pour payer des frais lorsque la limite de retrait est dépassée :

:::code language="csharp" source="./snippets/object-oriented-programming/LineOfCreditAccount.cs" ID="AddOverdraftFee":::

Le remplacement retourne une transaction de frais lorsque le compte est redessiné. Si le retrait n’excède pas la limite, la méthode retourne une `null` transaction. Cela indique qu’il n’y a aucun frais. Testez ces modifications en ajoutant le code suivant à votre `Main` méthode dans la `Program` classe :

:::code language="csharp" source="./snippets/object-oriented-programming/Program.cs" ID="TestLineOfCredit":::

Exécutez le programme et vérifiez les résultats.

## <a name="summary"></a>Résumé

Ce didacticiel a démontré de nombreuses techniques utilisées dans la programmation orientée objet :

- Vous avez utilisé l' *abstraction* quand vous avez conservé de nombreux détails `private` dans chaque classe.
- Vous avez utilisé l' *encapsulation* lorsque vous avez défini des classes pour chacun des différents types de compte. Ces classes décrivent le comportement de ce type de compte.
- Vous avez utilisé l' *héritage* lorsque vous tirez parti de l’implémentation déjà créée dans la `BankAccount` classe pour enregistrer le code.
- Vous avez utilisé le *polymorphisme* quand vous avez créé `virtual` des méthodes que les classes dérivées peuvent substituer pour créer un comportement spécifique pour ce type de compte.

Félicitations, vous avez terminé tout notre introduction aux didacticiels C#. Pour en savoir plus, consultez les [didacticiels](../index.md)suivants.
