---
title: Types de changements cassants
description: Découvrez comment .NET Core tente de maintenir la compatibilité pour les développeurs à travers les versions .NET, et quel type de changement est considéré comme un changement de rupture.
ms.date: 06/10/2019
ms.openlocfilehash: bf0cc35d69e6bb501640455604a99a1f48962c4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628590"
---
# <a name="changes-that-affect-compatibility"></a>Changements qui affectent la compatibilité

Tout au long de son histoire, .NET a tenté de maintenir un niveau élevé de compatibilité de version en version et entre les différentes déclinaisons de .NET. Cette philosophie s’applique toujours avec .NET Core. Bien que .NET Core peut être considéré comme une nouvelle technologie indépendante du .NET Framework, deux facteurs majeurs limitent la capacité de .NET Core à diverger du .NET Framework :

- Un grand nombre de développeurs ont développé à la base ou continuent à développer des applications .NET Framework. Ils s’attendent à un comportement cohérent entre les implémentations de .NET.

- Les projets de bibliothèque .NET Standard permettent aux développeurs de créer des bibliothèques qui ciblent les API communes partagées par .NET Core et .NET Framework. Les développeurs s’attendent à ce qu’une bibliothèque utilisée dans une application .NET Core se comporte comme la bibliothèque utilisée dans une application .NET Framework.

En plus de la compatibilité entre les implémentations de .NET, les développeurs s’attendent à un haut niveau de compatibilité entre les versions de .NET Core. En particulier, le code écrit pour une version antérieure de .NET Core doit s’exécuter sans problème sur une version ultérieure de .NET Core. En fait, de nombreux développeurs s’attendent à ce que les nouvelles API dans les dernières versions de .NET Core soient également compatibles avec les versions préliminaires dans lesquelles ces API ont été introduites.

Cet article décrit les catégories de modifications de compatibilité (ou changements cassants) et la manière dont l’équipe .NET évalue les modifications dans chacune de ces catégories. Comprendre comment l’équipe .NET aborde les changements de rupture possibles est particulièrement utile pour les développeurs qui ouvrent les demandes de traction dans le référentiel GitHub [pointnet/runtime](https://github.com/dotnet/runtime) qui modifient le comportement des API existantes.

> [!NOTE]
> Pour une définition des catégories de compatibilité, comme la compatibilité binaire et la compatibilité descendante, consultez [Catégories de changements cassants](categories.md).

Les sections suivantes décrivent les catégories de modifications apportées aux API de base .NET et leur impact sur la compatibilité des applications. Les changements sont soit autorisés ✔️, ❌refusés, ou nécessitent un jugement et une évaluation de la façon prévisible, évidente, et cohérente le comportement précédent a été ❓.

> [!NOTE]
> En plus de servir de guide pour l’évaluation des modifications apportées aux bibliothèques .NET Core, les développeurs de bibliothèques peuvent également utiliser ces critères pour évaluer les modifications apportées à leurs bibliothèques qui ciblent plusieurs implémentations et versions de .NET.

## <a name="modifications-to-the-public-contract"></a>Modifications au contrat public

Les modifications de cette catégorie modifient la surface d’exposition publique d’un type. La plupart des modifications de cette catégorie ne sont pas autorisées dans la mesure où elles enfreignent une *compatibilité descendante* (la possibilité pour une application qui a été développée avec une version précédente d’une API de s’exécuter sans recompilation sur une version ultérieure).

### <a name="types"></a>Types

- ✔️ ALLOWED **: Suppression d’une implémentation d’interface à partir d’un type lorsque l’interface est déjà implémentée par un type de base**

- ❓ **REQUIRES JUDGMENT: Ajout d’une nouvelle implémentation d’interface à un type**

  Il s’agit d’une modification acceptable, car elle n’affectera pas les clients existants. Toutes les modifications au type doivent fonctionner dans les limites des modifications acceptables définies ici pour la nouvelle implémentation afin de rester acceptables. Une prudence extrême est nécessaire lors de l’ajout d’interfaces qui affectent directement la capacité d’un concepteur ou sérialiseur à générer du code ou des données qui ne peuvent pas être consommées à un bas niveau. Par exemple, l’interface <xref:System.Runtime.Serialization.ISerializable>.

- ❓ REQUIRES **JUDGMENT: Présentation d’une nouvelle classe de base**

  Un type peut être introduit dans une hiérarchie entre deux types existants s’il n’introduit pas de nouveaux membres [abstraits](../../csharp/language-reference/keywords/abstract.md) ou ne modifie pas la sémantique ou le comportement des types existants. Par exemple, dans .NET Framework 2.0, la classe <xref:System.Data.Common.DbConnection> est devenue une classe de base pour <xref:System.Data.SqlClient.SqlConnection>, qui était précédemment dérivée directement de <xref:System.ComponentModel.Component>.

- ✔️ **ALLOWED: Déplacer un type d’une assemblée à l’autre**

  *L’ancienne* assemblée doit <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> être marquée par ce qui indique la nouvelle assemblée.

- ✔️ **ALLOWED: Changer un type de `readonly struct` [struction](../../csharp/language-reference/builtin-types/struct.md) en un type**

  La `readonly struct` modification d’un type à un `struct` type n’est pas autorisée.

- ✔️ ALLOWED **: Ajout du mot clé [scellé](../../csharp/language-reference/keywords/sealed.md) ou [abstrait](../../csharp/language-reference/keywords/abstract.md) à un type de type lorsqu’il n’y a pas de constructeurs *accessibles* (publics ou protégés)**

- ✔️ ALLOWED **: Élargir la visibilité d’un type**

- ❌**DISALLOWED: Changer l’espace de nom ou le nom d’un type**

- ❌**DISALLOWED: Renommer ou supprimer un type public**

   Cela empêche tout code qui utilise le type renommé ou supprimé de fonctionner.

- ❌**DISALLOWED: Changer le type sous-jacent d’un recensement**

   Il s’agit d’un changement cassant au niveau de la compilation et du comportement ainsi qu’un changement cassant binaire qui peut rendre les arguments d’attribut non analysables.

- ❌**DISALLOWED: Sceller un type qui a été précédemment non scellé**

- ❌**DISALLOWED: Ajout d’une interface à l’ensemble des types de base d’une interface**

   Si une interface implémente une interface qu’elle n’implémentait pas précédemment, tous les types implémentant la version d’origine de l’interface cessent de fonctionner.

- ❓ REQUIRES **JUDGMENT: Supprimer une classe de l’ensemble des classes de base ou une interface de l’ensemble des interfaces mises en œuvre**

  Il existe une exception à la règle pour la suppression de l’interface : vous pouvez ajouter l’implémentation d’une interface qui dérive de l’interface supprimée. Par exemple, vous pouvez supprimer <xref:System.IDisposable> si le type ou l’interface implémente désormais <xref:System.ComponentModel.IComponent>, qui implémente <xref:System.IDisposable>.

- ❌**DISALLOWED: Changer `readonly struct` un type à un type [de struct](../../csharp/language-reference/builtin-types/struct.md) **

  Le changement `struct` d’un `readonly struct` type à un type est toutefois autorisé.

- ❌**DISALLOWED: Changer un type `ref struct` [de struct à](../../csharp/language-reference/builtin-types/struct.md) un type, et vice versa**

- ❌**DISALLOWED: Réduire la visibilité d’un type**

   Toutefois, l’augmentation de la visibilité d’un type est autorisée.

### <a name="members"></a>Membres

- ✔️ ALLOWED **: Élargir la visibilité d’un membre qui n’est pas [virtuel](../../csharp/language-reference/keywords/sealed.md) **

- ✔️ ALLOWED **: Ajout d’un membre abstrait à un type public qui n’a pas de *constructeurs accessibles* (publics ou protégés), ou le type est [scellé](../../csharp/language-reference/keywords/sealed.md) **

  Toutefois, l’ajout à un membre abstrait à un type qui a des constructeurs accessibles (publics ou protégés) et n’est pas `sealed` n’est pas autorisé.

- ✔️ **ALLOWED : Restreindre la visibilité d’un membre [protégé](../../csharp/language-reference/keywords/protected.md) lorsque le type n’a pas de constructeurs accessibles (publics ou protégés), ou le type est [scellé](../../csharp/language-reference/keywords/sealed.md) **

- ✔️ **ALLOWED: Déplacer un membre dans une classe supérieure dans la hiérarchie que le type à partir duquel il a été supprimé**

- ✔️ **ALLOWED: Ajout ou suppression d’un remplacement**

  L’introduction d’un remplacement peut amener les consommateurs précédents à sauter par-dessus la dérogation lors de l’appel [de base](../../csharp/language-reference/keywords/base.md).

- ✔️ **ALLOWED: Ajout d’un constructeur à une classe, avec un constructeur sans paramètres si la classe n’avait auparavant pas de constructeurs**

   Cependant, ajouter un constructeur à une classe qui n’avait auparavant aucun constructeur *sans* ajouter le constructeur sans paramètre n’est pas autorisé.

- ✔️ **ALLOWED: Changer un membre [virtual](../../csharp/language-reference/keywords/virtual.md) de [l’abstrait](../../csharp/language-reference/keywords/abstract.md) au virtuel**

- ✔️ **ALLOWED: Passer `ref readonly` d’une valeur de retour à une `ref` valeur de retour (sauf pour les méthodes virtuelles ou les interfaces)**

- ✔️ **ALLOWED: Retrait [réaduté](../../csharp/language-reference/keywords/readonly.md) d’un champ, à moins que le type statique du champ soit un type de valeur mutable**

- ✔️ **ALLOWED: Appel d’un nouvel événement qui n’a pas été défini précédemment**

- ❓ **REQUIRES JUDGMENT: Ajout d’un nouveau champ d’instance à un type**

   Cette modification a un impact sur la sérialisation.

- ❌**DISALLOWED : Renommer ou supprimer un membre public ou un paramètre**

   Cela empêche tout code qui utilise le membre ou paramètre renommé ou supprimé de fonctionner.

   Cela comprend la suppression ou le changement de nom d’un getter ou d’un setter d’une propriété, ainsi que le changement de nom ou la suppression des membres de l’énumération.

- ❌**DISALLOWED: Ajout d’un membre à une interface**

- ❌**DISALLOWED: Changer la valeur d’un membre public constant ou de recensement**

- ❌**DISALLOWED: Modification du type de propriété, champ, paramètre, ou valeur de retour**

- ❌**DISALLOWED: Ajout, suppression ou modification de l’ordre des paramètres**

- ❌**DISALLOWED: Ajout ou suppression de [l’in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) , ou [ref](../../csharp/language-reference/keywords/ref.md) mot clé d’un paramètre**

- ❌**DISALLOWED: Renommer un paramètre (y compris changer son cas)**

  Cela est considéré comme un changement cassant pour deux raisons :

  - Cela empêche les scénarios à liaison tardive comme la fonctionnalité de liaison tardive de Visual Basic et [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) de C#.

  - Cela annule la [compatibilité de la source](categories.md#source-compatibility) lorsque les développeurs utilisent des [arguments nommés](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).

- ❌**DISALLOWED: Passer `ref` d’une `ref readonly` valeur de retour à une valeur de retour**

- ❌️**DISALLOWED: Passer `ref readonly` d’une valeur de retour à une `ref` méthode ou une interface virtuelle**

- ❌**DISALLOWED: Ajout ou suppression [de l’abstrait](../../csharp/language-reference/keywords/abstract.md) d’un membre**

- ❌**DISALLOWED: Supprimer le mot clé [virtuel](../../csharp/language-reference/keywords/virtual.md) d’un membre**

  Bien que cela n’est souvent pas un changement cassant, car le compilateur C# a tendance à émettre des instructions [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) en langage intermédiaire pour appeler des méthodes non virtuelles (`callvirt` effectue une vérification de valeur null, alors qu’un appel normal ne le fait pas), ce comportement n’est pas invariable pour plusieurs raisons :
  - C# n’est pas le seul langage que .NET cible.

  - Le compilateur C# essaie progressivement d’optimiser `callvirt` en un appel normal chaque fois que la méthode cible est non virtuelle et n’a probablement pas la valeur null (par exemple une méthode accessible via [l’opérateur de propagation de NULL ?](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).

  Rendre une méthode virtuelle signifie que le code consommateur finirait souvent par l’appeler de façon non virtuelle.

- ❌**DISALLOWED: Ajout du mot clé [virtuel](../../csharp/language-reference/keywords/virtual.md) à un membre**

- ❌**DISALLOWED: Rendre un membre virtuel abstrait**

  Un [membre virtuel](../../csharp/language-reference/keywords/virtual.md) fournit une implémentation de méthode qui *peut être* substituée par une classe dérivée. Un [membre abstrait](../../csharp/language-reference/keywords/abstract.md) ne fournit aucune implémentation et *doit être* substitué.

- ❌**DISALLOWED : Ajout d’un membre abstrait à un type public qui a des constructeurs accessibles (publics ou protégés) et qui n’est pas [scellé](../../csharp/language-reference/keywords/sealed.md) **

- ❌**DISALLOWED: Ajout ou suppression du mot clé [statique](../../csharp/language-reference/keywords/static.md) d’un membre**

- ❌**DISALLOWED: Ajout d’une surcharge qui empêche une surcharge existante et définit un comportement différent**

  Cela empêche de fonctionner les clients existants qui étaient liés à la surcharge précédente. Par exemple, si une classe a une seule version d’une méthode qui accepte un <xref:System.UInt32>, un consommateur existant est correctement lié à cette surcharge lors du passage d’une valeur <xref:System.Int32>. Toutefois, si vous ajoutez une surcharge qui accepte un <xref:System.Int32> lors de la recompilation ou à l’aide d’une liaison tardive, le compilateur est maintenant lié à la nouvelle surcharge. Si un comportement différent se produit, il s’agit d’un changement cassant.

- ❌**DISALLOWED: Ajout d’un constructeur à une classe qui n’avait auparavant pas de constructeur sans ajouter le constructeur sans paramètres**

- ❌️**DISALLOWED: Ajout [de lecture à](../../csharp/language-reference/keywords/readonly.md) un champ**

- ❌**DISALLOWED: Réduire la visibilité d’un membre**

   Cela comprend la réduction de la visibilité d’un membre [protégé](../../csharp/language-reference/keywords/protected.md) lorsqu’il y a des constructeurs *accessibles* `public` ( ou) `protected`et que le type *n’est pas* [scellé.](../../csharp/language-reference/keywords/sealed.md) Si ce n’est pas le cas, la réduction de la visibilité d’un membre protégé est autorisée.

   L’augmentation de la visibilité d’un membre est permise.

- ❌**DISALLOWED: Changer le type de membre**

   La valeur renvoyée d’une méthode ou le type d’une propriété ou d’un champ ne peut pas être modifiée. Par exemple, la signature d’une méthode qui retourne un <xref:System.Object> ne peut pas être modifiée afin de retourner un <xref:System.String>, ou vice versa.

- ❌**DISALLOWED: Ajout d’un champ à une structure qui n’avait auparavant pas d’état**

  Les règles d’affectation autorisent l’utilisation de variables non initialisées tant que le type de variable est un struct sans état. Si le struct est avec état, le code pourrait se retrouver avec des données non initialisées. Il s’agit potentiellement d’un changement cassant binaire et d’un changement cassant source.

- ❌**DISALLOWED: Tirer un événement existant quand il n’a jamais été tiré avant**

## <a name="behavioral-changes"></a>Changements de comportement

### <a name="assemblies"></a>Assemblys

- ✔️ **ALLOWED: Rendre un assemblage portable lorsque les mêmes plates-formes sont encore prises en charge**

- ❌**DISALLOWED: Changer le nom d’une assemblée**
- ❌**DISALLOWED: Changer la clé publique d’une assemblée**

### <a name="properties-fields-parameters-and-return-values"></a>Propriétés, champs, paramètres et valeurs renvoyées

- ✔️ ALLOWED **: Modification de la valeur d’une propriété, d’un champ, d’une valeur de rendement ou [d’un](../../csharp/language-reference/keywords/out-parameter-modifier.md) paramètre à un type plus dérivé**

  Par exemple, une méthode qui retourne un type <xref:System.Object> peut retourner une instance de <xref:System.String>. (Toutefois, la signature de méthode ne peut pas être modifiée).

- ✔️ **ALLOWED: Augmenter la gamme de valeurs acceptées pour une propriété ou un paramètre si le membre n’est pas [virtuel](../../csharp/language-reference/keywords/virtual.md) **

  Bien que la gamme de valeurs qui peuvent être transmises à la méthode ou retournées par le membre peut s’étendre, le paramètre ou le type de membre ne peut pas. Par exemple, tandis que les valeurs passées à une méthode peuvent s’étendre de 0-124 à 0-255, le type de paramètre ne peut pas être changé de <xref:System.Byte> à <xref:System.Int32>.

- ❌**DISALLOWED: Augmenter la gamme de valeurs acceptées pour une propriété ou un paramètre si le membre est [virtuel](../../csharp/language-reference/keywords/virtual.md) **

   Ce changement empêche le fonctionnement des membres substitués existants, qui ne fonctionneront pas correctement pour la plage de valeurs étendue.

- ❌**DISALLOWED: Diminution de la gamme de valeurs acceptées pour une propriété ou un paramètre**

- ❌**DISALLOWED: Augmentation de la gamme de valeurs retournées pour une propriété, un champ, une valeur de rendement ou [un](../../csharp/language-reference/keywords/out-parameter-modifier.md) paramètre**

- ❌**DISALLOWED: Modification des valeurs retournées pour une propriété, un champ, une valeur de rendement de la méthode ou [un](../../csharp/language-reference/keywords/out-parameter-modifier.md) paramètre**

- ❌**DISALLOWED: Modification de la valeur par défaut d’une propriété, d’un champ ou d’un paramètre**

- ❌**DISALLOWED: Changer la précision d’une valeur de rendement numérique**

- ❓ **REQUIRES JUDGMENT: Un changement dans l’analyse de l’entrée et de jeter de nouvelles exceptions (même si le comportement d’analyse n’est pas spécifié dans la documentation**

### <a name="exceptions"></a>Exceptions

- ✔️ **ALLOWED: Jeter une exception plus dérivée qu’une exception existante**

  Étant donné que la nouvelle exception est une sous-classe d’une exception existante, le code de gestion des exceptions précédent continue à gérer l’exception. Par exemple, dans .NET Framework 4, les méthodes de création et de récupération de culture ont commencé à lever un <xref:System.Globalization.CultureNotFoundException> au lieu d’un <xref:System.ArgumentException> si la culture est introuvable. Étant donné que <xref:System.Globalization.CultureNotFoundException> dérive de <xref:System.ArgumentException>, il s’agit d’une modification acceptable.

- ✔️ **ALLOWED: Jeter une exception plus <xref:System.NotSupportedException> <xref:System.NotImplementedException>spécifique <xref:System.NullReferenceException> que , ,**

- ✔️ **ALLOWED: Jeter une exception jugée irrécupérable**

  Les exceptions irrécupérables ne doivent pas être interceptées, mais plutôt être gérées par un gestionnaire fourre-tout de haut niveau. Par conséquent, les utilisateurs ne sont pas censés avoir du code qui intercepte les exceptions explicites. Les exceptions irrécupérables sont :

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- ✔️ **ALLOWED: Jeter une nouvelle exception dans un nouveau chemin de code**

  L’exception ne doit s’appliquer qu’à un nouveau code-chemin qui est exécuté avec de nouvelles valeurs de paramètres ou d’état et qui ne peut pas être exécuté par le code existant qui cible la version précédente.

- ✔️ **ALLOWED: Suppression d’une exception pour permettre un comportement plus robuste ou de nouveaux scénarios**

  Par exemple, une méthode `Divide` qui pouvait auparavant uniquement gérer des valeurs positives et levait un <xref:System.ArgumentOutOfRangeException> peut être modifiée pour prendre en charge les valeurs positives et négatives sans lever d’exception.

- ✔️ **ALLOWED: Changer le texte d’un message d’erreur**

  Les développeurs ne doivent pas compter sur le texte des messages d’erreur, qui changent également selon la culture de l’utilisateur.

- ❌**DISALLOWED: Jeter une exception dans tout autre cas non répertorié ci-dessus**

- ❌**DISALLOWED: Suppression d’une exception dans tout autre cas non répertorié ci-dessus**

### <a name="attributes"></a>Attributs

- ✔️ **ALLOWED: Changer la valeur d’un attribut qui *n’est pas* observable**

- ❌**DISALLOWED: Changer la valeur d’un attribut qui *est* observable**

- ❓ REQUIRES **JUDGMENT: Suppression d’un attribut**

  Dans la plupart des cas, la suppression d’un attribut (comme <xref:System.NonSerializedAttribute>) est un changement cassant.

## <a name="platform-support"></a>Plateforme prise en charge

- ✔️ **ALLOWED: Soutenir une opération sur une plate-forme qui n’était pas auparavant prise en charge**

- ❌**DISALLOWED: Ne pas soutenir ou maintenant exiger un pack de service spécifique pour une opération qui a été précédemment pris en charge sur une plate-forme**

## <a name="internal-implementation-changes"></a>Modifications de l’implémentation interne

- ❓ REQUIRES **JUDGMENT: Changer la surface d’un type interne**

   Ces modifications sont généralement autorisées, même si elles rompent la réflexion privée. Dans certains cas, où les bibliothèques tierces les plus courantes ou un grand nombre de développeurs dépendent d’API internes, ces modifications ne peuvent pas être autorisées.

- ❓ REQUIRES **JUDGMENT: Changer la mise en œuvre interne d’un membre**

  Ces modifications sont généralement autorisées, même si elles rompent la réflexion privée. Dans certains cas où le code du client dépend souvent de la réflexion privée ou où la modification introduit des effets secondaires involontaires, ces modifications peuvent ne pas être autorisées.

- ✔️ ALLOWED **: Améliorer les performances d’une opération**

   La possibilité de modifier les performances d’une opération est essentielle, mais ces modifications peuvent endommager le code repose sur la vitesse actuelle d’une opération. Cela est particulièrement vrai pour du code qui dépend de la chronologie des opérations asynchrones. Le changement de performance ne devrait avoir aucun effet sur d’autres comportements de l’API en question; sinon, le changement sera rompu.

- ✔️ **ALLOWED: Modifier indirectement (et souvent négativement) la performance d’une opération**

  Si la modification en question n’est pas considérée comme un changement cassant pour une raison quelconque, cela est acceptable. Souvent, des mesures doivent être prises, ce qui peut inclure des opérations supplémentaires ou l’ajout de nouvelles fonctionnalités. Cela affectera presque toujours les performances, mais peut s’avérer essentiel pour que l’API en question fonctionne comme prévu.

- ❌**DISALLOWED: Changer une API synchrone à asynchrone (et vice versa)**

## <a name="code-changes"></a>Modifications du code

- ✔️ **ALLOWED: Ajout [de params](../../csharp/language-reference/keywords/params.md) à un paramètre**

- ❌**DISALLOWED: Changer une [structure](../../csharp/language-reference/builtin-types/struct.md) en [classe](../../csharp/language-reference/keywords/class.md) et vice versa**

- ❌**DISALLOWED: Ajout du mot clé [vérifié](../../csharp/language-reference/keywords/virtual.md) à un bloc de code**

   Cette modification peut pousser le code précédemment exécuté à lever <xref:System.OverflowException>, ce qui n’est pas acceptable.

- ❌**DISALLOWED: Suppression des [params](../../csharp/language-reference/keywords/params.md) d’un paramètre**

- ❌**DISALLOWED: Changer l’ordre dans lequel les événements sont déclenchés**

  Les développeurs peuvent raisonnablement s’attendre à ce que les événements se déclenchent dans le même ordre, et le code développeur dépend souvent de l’ordre dans lequel les événements sont déclenchés.

- ❌**DISALLOWED: Suppression de la levée d’un événement sur une action donnée**

- ❌**DISALLOWED: Changer le nombre de fois que les événements donnés sont appelés**

- ❌**DISALLOWED: Ajout <xref:System.FlagsAttribute> de l’un type d’énumération**
