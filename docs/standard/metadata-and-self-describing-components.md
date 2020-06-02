---
title: Métadonnées et composants autodescriptifs
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- runtime, metadata
- languages, interoperability
- portable executable files, metadata
- self-describing files
- metadata, about metadata
- common language runtime, metadata
- PE files, metadata
- components [.NET Framework], metadata
ms.assetid: 3dd13c5d-a508-455b-8dce-0a852882a5a7
ms.openlocfilehash: 5327bd70b05bac8970fa9802fb15e94ba5f686c8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290056"
---
# <a name="metadata-and-self-describing-components"></a>Métadonnées et composants autodescriptifs

Par le passé, un composant logiciel (.exe or .dll) écrit dans un langage ne pouvait pas utiliser aisément un composant logiciel écrit dans un autre langage. COM a fourni une étape vers la résolution de ce problème. Le .NET Framework facilite encore plus l'interopérabilité des composants en autorisant les compilateurs à émettre des informations déclaratives supplémentaires dans tous les modules et assemblys. Ces informations, appelées métadonnées, aident les composants à interagir de façon transparente.

 Les métadonnées sont des informations binaires décrivant votre programme ; elles sont stockées dans un fichier exécutable portable (fichier PE) du Common Language Runtime ou en mémoire. Lorsque vous compilez votre code dans un fichier PE, les métadonnées sont insérées dans une partie du fichier, tandis que votre code est converti en langage MSIL (Microsoft Intermediate Language) et inséré dans une autre partie du fichier. Les types et membre définis et référencés dans un module ou un assembly sont décrits au sein des métadonnées. Quand le code est exécuté, le runtime charge les métadonnées en mémoire et y fait référence pour découvrir les informations concernant les classes de votre code, les membres, l'héritage, etc.

 Les métadonnées décrivent tous les types et membres définis dans votre code sous une forme indépendante du langage. Les métadonnées stockent les informations suivantes :

- Description de l'assembly.

  - Identité (nom, version, culture, clé publique).

  - Les types exportés.

  - Les autres assemblys dont dépend cet assembly.

  - Les autorisations de sécurité nécessaires à l'exécution.

- Description des types.

  - Nom, visibilité, classe de base et interfaces implémentées.

  - Membres (méthodes, champs, propriétés, événements, types imbriqués).

- Attributs.

  - Éléments descriptifs supplémentaires qui modifient les types et les membres.

## <a name="benefits-of-metadata"></a>Avantages des métadonnées

Les métadonnées sont la clé d'un modèle de programmation plus simple et suppriment la nécessité de fichiers IDL (Interface Definition Language), de fichiers d'en-tête ou de toute méthode externe de référence aux composants. Les métadonnées permettent aux langages du .NET Framework de se décrire eux-mêmes automatiquement d'une manière indépendante du langage, transparente aussi bien au développeur qu'à l'utilisateur. En outre, les métadonnées sont extensibles via l'utilisation d'attributs. Les métadonnées offrent les principaux avantages suivants :

- Fichiers autodescriptifs.

  Les modules et assemblys du Common Language Runtime sont autodescriptifs. Les métadonnées d'un module contiennent tous les éléments nécessaires pour interagir avec un autre module. Les métadonnées offrent automatiquement la fonctionnalité IDL du modèle COM, ce qui vous permet d'utiliser un seul fichier pour la définition et l'implémentation. Les modules et assemblys du runtime ne nécessitent même pas l'inscription dans le système d'exploitation. En conséquence, les descriptions utilisées par le runtime reflètent toujours le code réel de votre fichier compilé, ce qui accroît la fiabilité de l'application.

- Interopérabilité des langages et design à base de composants plus simple.

  Les métadonnées fournissent toutes les informations requises concernant le code compilé pour que vous puissiez hériter une classe à partir d'un fichier PE écrit dans un autre langage. Vous pouvez créer une instance de toute classe écrite dans un langage managé (tout langage ciblant le Common Language Runtime) sans vous préoccuper de marshaling explicite ou d'utiliser un code d'interopérabilité personnalisé.

- Attributs.

  Le .NET Framework vous permet de déclarer des types particuliers de métadonnées, appelés attributs, dans votre fichier compilé. Les attributs peuvent être recherchés via le .NET Framework et sont utilisés pour contrôler de façon plus détaillée comment votre programme se comporte au moment de l'exécution. En outre, vous pouvez émettre vos propres métadonnées personnalisées dans les fichiers .NET Framework via les attributs personnalisés définis par l'utilisateur. Pour plus d’informations, consultez [Attributs](attributes/index.md).

## <a name="metadata-and-the-pe-file-structure"></a>Métadonnées et structure des fichiers PE

Les métadonnées sont stockées dans une section du fichier exécutable portable (fichier PE) .NET Framework, tandis que le code MSIL (Microsoft Intermediate Language) est stocké dans une autre section. La partie métadonnées du fichier contient un ensemble de structures de données de table et de tas. La partie MSIL contient le code MSIL et les jetons de métadonnées qui font référence à la partie métadonnées du fichier PE. Vous pouvez rencontrer des jetons de métadonnées quand vous utilisez des outils tels que le [Désassembleur MSIL (Ildasm.exe)](../framework/tools/ildasm-exe-il-disassembler.md) pour consulter le MSIL de votre code, par exemple.

### <a name="metadata-tables-and-heaps"></a>Tas et tables de métadonnées

Chaque table de métadonnées contient des informations sur les éléments de votre programme. Par exemple, une table de métadonnées décrit les classes de votre code, une autre décrit les champs, etc. Si vous disposez de dix classes dans votre code, la table des classes aura dix lignes, une par classe. Les tables de métadonnées font référence à d'autres tables et d'autres tas. Par exemple, la table des métadonnées pour les classes fait référence à la table pour les méthodes.

Les métadonnées stockent aussi des informations dans quatre structures de tas : chaîne, blob, chaîne utilisateur et un Identificateur Global Unique (GUID, Globally Unique IDentifier). Toutes les chaînes utilisées pour nommer les types et les membres sont stockées dans le tas de chaîne. Par exemple, une table de méthodes ne stocke pas directement le nom d'une méthode particulière, mais pointe vers le nom de la méthode stocké dans le tas de chaîne.

### <a name="metadata-tokens"></a>Jetons de métadonnées

Chaque ligne des tables de métadonnées est identifiée de façon unique dans la partie MSIL du fichier PE au moyen d'un jeton de métadonnées. Conceptuellement, les jetons de métadonnées sont similaires à des pointeurs, persistants dans le langage MSIL, qui font référence à une table de métadonnées spécifique.

Un jeton de métadonnées est un nombre stocké sur quatre octets. L'octet de poids le plus fort identifie la table de métadonnées à laquelle un jeton donné fait référence (méthode, type, etc.). Les trois octets restants spécifient la ligne de la table de métadonnées qui correspond à l'élément de programmation en cours de description. Si vous définissez une méthode en C# et la compilez dans un fichier PE, le jeton de métadonnées suivant figurera probablement dans la partie MSIL du fichier PE :

`0x06000004`

L’octet de poids le plus fort (`0x06`) indique qu’il s’agit d’un jeton **MethodDef**. Les trois autres octets (`000004`) indiquent au Common Language Runtime de rechercher dans la quatrième ligne de la table **MethodDef** les informations décrivant la définition de cette méthode.

### <a name="metadata-within-a-pe-file"></a>Métadonnées au sein d'un fichier PE

Quand un programme est compilé pour le Common Language Runtime, il est converti en fichier PE, composé de trois parties. Le tableau ci-après décrit le contenu de chaque partie.

|Section PE|Contenu de la section PE|
|----------------|----------------------------|
|En-tête PE|L'index des sections principales du fichier PE et l'adresse du point d'entrée.<br /><br /> Le runtime utilise ces informations pour identifier le fichier comme fichier PE et pour déterminer où commence l'exécution lors du chargement du programme en mémoire.|
|Instructions MSIL|Les instructions MSIL (Microsoft Intermediate Language) composant votre code. Nombre d'instructions MSIL sont accompagnées de jetons de métadonnées.|
|Métadonnées|Tas et tables de métadonnées. Le runtime utilise cette section pour enregistrer les informations sur chaque type et membre de votre code. Cette section contient aussi des attributs personnalisés et des informations de sécurité.|

## <a name="run-time-use-of-metadata"></a>Utilisation de métadonnées au moment de l'exécution

Pour mieux comprendre les métadonnées et leur rôle dans le Common Language Runtime, il peut être utile de construire un programme simple qui illustre comment les métadonnées influencent son comportement à l'exécution. L'exemple de code suivant montre deux méthodes à l'intérieur d'une classe intitulée `MyApp`. La méthode `Main` constitue le point d’entrée du programme, tandis que la méthode `Add` retourne simplement le total de deux arguments de type entier.

```vb
Public Class MyApp
   Public Shared Sub Main()
      Dim ValueOne As Integer = 10
      Dim ValueTwo As Integer = 20
      Console.WriteLine("The Value is: {0}", Add(ValueOne, ValueTwo))
   End Sub

   Public Shared Function Add(One As Integer, Two As Integer) As Integer
      Return (One + Two)
   End Function
End Class
```

```csharp
using System;
public class MyApp
{
   public static int Main()
   {
      int ValueOne = 10;
      int ValueTwo = 20;
      Console.WriteLine("The Value is: {0}", Add(ValueOne, ValueTwo));
      return 0;
   }
   public static int Add(int One, int Two)
   {
      return (One + Two);
   }
}
```

Quand le code s'exécute, le runtime charge le module en mémoire et consulte les métadonnées correspondant à la classe. Une fois chargé, le runtime effectue une analyse complète du flux MSIL de la méthode pour le convertir en instructions machine natives rapides. Le runtime utilise un compilateur juste-à-temps (JIT, Just-In-Time) pour convertir les instructions MSIL en code machine natif, une méthode à la fois, selon les besoins.

L'exemple suivant montre une partie du MSIL générée à partir de la fonction `Main` du code précédent. Vous pouvez afficher le code MSIL et les métadonnées de toute application .NET Framework à l’aide du [Désassembleur MSIL (Ildasm.exe)](../framework/tools/ildasm-exe-il-disassembler.md).

```console
.entrypoint
.maxstack  3
.locals ([0] int32 ValueOne,
         [1] int32 ValueTwo,
         [2] int32 V_2,
         [3] int32 V_3)
IL_0000:  ldc.i4.s   10
IL_0002:  stloc.0
IL_0003:  ldc.i4.s   20
IL_0005:  stloc.1
IL_0006:  ldstr      "The Value is: {0}"
IL_000b:  ldloc.0
IL_000c:  ldloc.1
IL_000d:  call int32 ConsoleApplication.MyApp::Add(int32,int32) /* 06000003 */
```

Le compilateur JIT lit le code MSIL de la totalité de la méthode, l'analyse intégralement et génère des instructions natives performantes pour la méthode. L’adresse `IL_000d` contient un jeton de métadonnées pour la méthode `Add` (`/*` `06000003 */`) et le runtime utilise ce jeton pour consulter la troisième ligne de la table **MethodDef**.

Le tableau suivant montre une partie de la table **MethodDef** référencée par le jeton de métadonnées qui décrit la méthode `Add`. Bien qu'il existe d'autres tables de métadonnées dans cet assembly et qu'elles aient leurs propres valeurs uniques, seule cette table est prise en compte dans le tableau.

|Ligne|Adresse RVA (Relative Virtual Address)|ImplFlags|Indicateurs|Nom<br /><br /> (pointe vers le tas de chaîne)|Signature (pointe vers le tas de blob)|
|---------|--------------------------------------|---------------|-----------|-----------------------------------------|----------------------------------------|
|1|0x00002050|IL<br /><br /> Géré|Public<br /><br /> ReuseSlot<br /><br /> SpecialName<br /><br /> RTSpecialName<br /><br /> .ctor|.ctor (constructeur)||
|2|0x00002058|IL<br /><br /> Géré|Public<br /><br /> statique<br /><br /> ReuseSlot|Principal|String|
|3|0x0000208c|IL<br /><br /> Géré|Public<br /><br /> statique<br /><br /> ReuseSlot|Ajouter|int, int, int|

Chaque colonne de la table contient des informations importantes concernant votre code. La colonne **RVA** permet au runtime de calculer l’adresse mémoire de départ du code MSIL qui définit la méthode. Les colonnes **ImplFlags** et **Flags** contiennent des masques de bits qui décrivent la méthode (par exemple, ils indiquent si la méthode est publique ou privée). La colonne **Name** indexe le nom de la méthode à partir du tas de chaîne. La colonne **Signature** indexe la définition de la signature de la méthode dans le tas de blob.

Le runtime calcule l’adresse offset souhaitée à partir de la troisième ligne de la colonne **RVA** et retourne cette adresse au compilateur JIT, qui poursuit alors jusqu’à la nouvelle adresse. Le compilateur JIT continue le traitement du code MSIL à la nouvelle adresse jusqu'à ce qu'il rencontre un autre jeton de métadonnées, auquel cas le processus est répété.

Grâce aux métadonnées, le runtime a accès à toutes les informations dont il a besoin pour charger votre code et le traiter en instructions machine natives. Les métadonnées permettent ainsi les fichiers autodescriptifs et, en même temps que le système de type commun (CTS, Common Type System), l'héritage interlangage.

## <a name="related-topics"></a>Rubriques connexes

|Intitulé|Description|
|-----------|-----------------|
|[Attributs](attributes/index.md)|Décrit comment appliquer les attributs, écrire des attributs personnalisés et récupérer les informations stockées dans les attributs.|
