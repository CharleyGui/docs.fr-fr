---
title: Ildasm.exe (Désassembleur IL)
ms.date: 03/30/2017
helpviewer_keywords:
- PE files, MSIL Disassembler
- portable executable files, MSIL Disassembler
- Ildasm.exe
- MSIL Disassembler
- text files produced by MSIL Disassembler
- disassembling file for MSIL Assembler input
ms.assetid: db27f6b2-f1ec-499e-be3a-7eecf95ca42b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2239b73eb8418d469085ad72b8a28093146a1f6b
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025967"
---
# <a name="ildasmexe-il-disassembler"></a>Ildasm.exe (Désassembleur IL)

Le Désassembleur IL est un outil associé à l'Assembleur IL (*Ilasm.exe*). *Ildasm.exe* crée, à partir d'un fichier exécutable portable (PE) contenant du code IL (intermediate language), un fichier texte pouvant servir d'entrée dans *Ilasm.exe*.

Cet outil est installé automatiquement avec Visual Studio. Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7). Pour plus d'informations, consultez [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

À l'invite de commandes, tapez le texte suivant :

## <a name="syntax"></a>Syntaxe

```
ildasm [options] [PEfilename] [options]
```

## <a name="parameters"></a>Paramètres

Les options suivantes sont disponibles pour les fichiers *.exe*, *.dll*, *.obj*, *.lib* et *.winmd*.

| Option | Description |
| ------ | ----------- |
|**/out=** `filename`|Crée un fichier de sortie avec le `filename` spécifié, au lieu d’afficher les résultats dans une interface graphique utilisateur.|
|**/rtf**|Produit la sortie au format RTF. Non valide avec l’option **/text**.|
|**/text**|Affiche les résultats dans la fenêtre de console, plutôt que dans une interface graphique utilisateur ou dans un fichier de sortie.|
|**/html**|Produit la sortie au format HTML. Valide avec l’option **/output** uniquement.|
|**/?**|Affiche la syntaxe de commande et les options de l'outil.|

Les options suivantes sont également disponibles pour les fichiers *.exe*, *.dll* et *.winmd*.

| Option | Description |
| ------ | ----------- |
|**/bytes**|Affiche les octets actuels, au format hexadécimal, sous forme de commentaires d'instructions.|
|**/caverbal**|Produit des blobs d'attribut personnalisés sous forme verbale. La valeur par défaut est la forme binaire.|
|**/linenum**|Inclut des références dans les lignes sources d'origine.|
|**/nobar**|Supprime la fenêtre pop-up de l'indicateur de progression du code machine.|
|**/noca**|Supprime la sortie d'attributs personnalisés.|
|**/project**|Affiche les métadonnées telles qu'elles apparaissent dans le code managé, plutôt que telles qu'elles apparaissent dans le Windows Runtime natif. Si `PEfilename` n'est pas un fichier de métadonnées Windows ( *.winmd*), cette option n'a aucun effet. Consultez [Prise en charge .NET Framework pour les applications Windows Store et Windows Runtime](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).|
|**/pubonly**|Désassemble uniquement les membres et les types publics. Équivaut à **/visibility:PUB**.|
|**/quoteallnames**|Entoure tous les noms de guillemets simples.|
|**/raweh**|Affiche les clauses de gestion des exceptions sous une forme brute.|
|**/source**|Affiche les lignes sources d'origine sous forme de commentaires.|
|**/tokens**|Affiche les jetons de métadonnées des classes et des membres.|
|**/visibility:** `vis`[+`vis`...]|Désassemble uniquement les types ou les membres avec la visibilité spécifiée. Les valeurs valides pour `vis` sont les suivantes :<br /><br /> **PUB** — Public<br /><br /> **PRI** — Privé<br /><br /> **FAM** — Famille<br /><br /> **ASM** — Assembly<br /><br /> **FAA** — Famille et Assembly<br /><br /> **FOA** — Famille ou Assembly<br /><br /> **PSC** — Portée privée<br /><br /> Pour obtenir des définitions de ces modificateurs de visibilité, consultez <xref:System.Reflection.MethodAttributes> et <xref:System.Reflection.TypeAttributes>.|

Les options suivantes sont valides pour les fichiers *.exe*, *.dll* et *.winmd* uniquement à des fins de sortie vers une console ou un fichier uniquement.

| Option | Description |
| ------ | ----------- |
|**/all**|Spécifie une combinaison des options **/header**, **/bytes**, **/stats**, **/classlist** et **/tokens**.|
|**/classlist**|Inclut une liste de classes définie dans le module.|
|**/forward**|Utilise la déclaration de classe anticipée.|
|**/headers**|Inclut les informations d'en-tête du fichier dans la sortie.|
|**/item:** `class`[ **::** `member`[`(sig`]]|Désassemble les éléments suivants en fonction de l’argument fourni :<br /><br /> -   Désassemble la `class` spécifiée.<br />-   Désassemble le `member` spécifié de la `class`.<br />-   Désassemble le `member` de la `class` avec la signature spécifiée `sig`. Le format de `sig` est le suivant :<br />     [`instance`] `returnType`(`parameterType1`, `parameterType2`, …, `parameterTypeN`)<br />     **Remarque** Dans les versions 1.0 et 1.1 du .NET Framework, `sig` doit être suivi d’une parenthèse fermante : `(sig)`. À compter de .NET Framework 2.0, la parenthèse fermante doit être omise : `(sig`.|
|**/noil**|Supprime la sortie du code d'assembly IL.|
|**/stats**|Inclut des statistiques sur l'image.|
|**/typelist**|Produit la liste complète des types afin de conserver le classement des types dans un aller-retour.|
|**/unicode**|Utilise l'encodage Unicode pour la sortie.|
|**/utf8**|Utilise l'encodage UTF-8 pour la sortie. ANSI est la valeur par défaut.|

Les options suivantes sont valides pour les fichiers *.exe*, *.dll*, *.obj*, *.lib* et *.winmd* uniquement pour la sortie vers le fichier ou vers la console.

| Option | Description |
| ------ | ----------- |
|**/metadata**[=`specifier`]|Affiche les métadonnées, où `specifier` est :<br /><br /> **MDHEADER** — Affiche les informations d’en-tête et de taille des métadonnées.<br /><br /> **HEX** — Affiche les informations en hexadécimales ainsi qu’en mots.<br /><br /> **CSV** — Affiche les nombres d’enregistrements et les tailles de tas.<br /><br /> **UNREX** — Affiche les externes non résolus.<br /><br /> **SCHEMA** — Affiche les informations relatives au schéma et à l’en-tête des métadonnées.<br /><br /> **RAW** — Affiche les tables de métadonnées brutes.<br /><br /> **HEAPS** — Affiche les tas bruts.<br /><br /> **VALIDATE** — Valide la cohérence des métadonnées.<br /><br /> Vous pouvez spécifier plusieurs fois **/metadata**, avec des valeurs différentes pour `specifier`.|

Les options suivantes sont valides pour les fichiers *.lib* uniquement pour la sortie vers la console ou vers le fichier.

| Option | Description |
| ------ | ----------- |
|**/objectfile**=`filename`|Affiche les métadonnées d'un fichier objet seul dans la bibliothèque spécifiée.|

> [!NOTE]
> Aucune option d’*Ildasm.exe* ne respecte pas la casse et toutes sont reconnues à leurs trois premières lettres. Par exemple, **/quo** est équivalent à **/quoteallnames**. Les options spécifiant des arguments prennent en charge les deux-points (:) ou le signe égal (=) en tant que séparateur entre l'option et l'argument. Par exemple, **/output:** *filename* équivaut à **/output=** *filename*.

## <a name="remarks"></a>Remarques

*Ildasm.exe* ne fonctionne qu'avec des fichiers exécutables portables stockés sur le disque. Il ne fonctionne pas avec des fichiers installés dans le Global Assembly Cache.

Le fichier texte généré par *Ildasm.exe* peut servir d'entrée dans l'Assembleur IL (*Ilasm.exe*). Cet outil s'avère, par exemple, utile lors de la compilation d'un code dans un langage de programmation ne prenant pas en charge tous les attributs de métadonnées du runtime. Une fois le code compilé et la sortie exécutée via *Ildasm.exe*, le fichier texte IL obtenu peut être modifié manuellement pour y ajouter les attributs manquants. Vous pouvez ensuite exécuter ce fichier texte via l'Assembleur IL pour générer un fichier exécutable final.

> [!NOTE]
> Actuellement, vous ne pouvez pas utiliser cette technique avec des fichiers exécutables portables qui contiennent du code natif incorporé (par exemple, des fichiers exécutables portables générés par Visual C++).  

Vous pouvez utiliser l’interface graphique utilisateur par défaut du Désassembleur IL pour afficher, sous forme d’arborescence, le code désassemblé et les métadonnées de tout fichier exécutable portable existant. Pour utiliser l’interface graphique utilisateur, tapez **ildasm** au niveau de la ligne de commande sans préciser l’argument *PEfilename* ni d’options. Dans le menu **Fichier**, vous pouvez naviguer jusqu’au fichier PE que vous souhaitez charger dans *Ildasm.exe*. Pour enregistrer les métadonnées et le code désassemblé affichés pour le PE sélectionné, sélectionnez la commande **Dump** dans le menu **Fichier**. Pour enregistrer uniquement l’affichage d’arborescence hiérarchique, sélectionnez la commande **Dump de l’arborescence** dans le menu **Fichier**. Pour plus d’informations sur le chargement d’un fichier dans *Ildasm.exe* et l’interprétation de la sortie, consultez le didacticiel *Ildasm.exe*, qui se trouve dans le dossier Samples fourni avec le kit de développement logiciel (SDK) Windows.

Si vous utilisez *Ildasm.exe* avec un argument *PEfilename* comportant des ressources incorporées, l’outil génère alors plusieurs fichiers de sortie : un fichier texte comprenant du code IL et, pour chaque ressource managée incorporée, un fichier .resources généré à l’aide du nom de la ressource issu des métadonnées. Si une ressource non managée est incorporée dans *PEfilename*, un fichier .res est généré à l’aide du nom de fichier spécifié pour la sortie IL par l’option **/output**.

> [!NOTE]
> *Ildasm.exe* affiche uniquement les descriptions des métadonnées des fichiers d’entrée *.obj* et *.lib*. Le code IL de ces types de fichiers n'est pas désassemblé.

Vous pouvez exécuter *Ildasm.exe* sur un fichier .exe ou *.dll* pour déterminer s’il s’agit d’un fichier managé. Si le fichier n'est pas managé, l'outil affiche un message indiquant que le fichier ne contient pas d'en-tête du Common Language Runtime valide et qu'il ne peut pas être désassemblé. S'il s'agit d'un fichier managé, l'outil s'exécute correctement.

## <a name="version-information"></a>Informations sur la version

À compter de .NET Framework 4.5, *Ildasm.exe* gère un objet blob (Binary Large Object) marshal non reconnu en affichant le contenu binaire brut. Par exemple, le code suivant montre comment un BLOB marshal généré par un programme C# s'affiche :

```csharp
public void Test([MarshalAs((short)70)] int test) { }
```

```
// IL from Ildasm.exe output
.method public hidebysig instance void Test(int32  marshal({ 46 }) test) cil managed
```

À compter de .NET Framework 4.5, *Ildasm.exe* affiche les attributs qui sont appliqués aux implémentations d’interfaces, comme indiqué dans l’extrait suivant de la sortie du fichier *Ildasm.exe* :

```
.class public auto ansi beforefieldinit MyClass
  extends [mscorlib]System.Object
  implements IMyInterface
  {
    .interfaceimpl type IMyInterface
    .custom instance void
      [mscorlib]System.Diagnostics.DebuggerNonUserCodeAttribute::.ctor() = ( 01 00 00 00 )
      …
```

## <a name="examples"></a>Exemples

La commande suivante affiche les métadonnées et le code désassemblé du fichier PE `MyHello.exe` dans l’interface graphique utilisateur par défaut d’*Ildasm.exe*.

```console
ildasm myHello.exe
```

La commande suivante désassemble le fichier `MyFile.exe` et enregistre le texte de l'Assembleur IL obtenu dans le fichier *MyFile.il*.

```console
ildasm MyFile.exe /output:MyFile.il
```

La commande suivante désassemble le fichier `MyFile.exe` et affiche le texte de l'Assembleur IL obtenu dans la fenêtre de console.

```console
ildasm MyFile.exe /text
```

Si le fichier `MyApp.exe` intègre des ressources managées et non managées, la commande suivante génère quatre fichiers : *MyApp.il*, *MyApp.res*, *Icons.resources* et *Message.resources* :

```console
ildasm MyApp.exe /output:MyApp.il
```

La commande suivante désassemble la méthode `MyMethod` figurant dans la classe `MyClass` de `MyFile.exe` et affiche la sortie dans la fenêtre de console.

```console
ildasm /item:MyClass::MyMethod MyFile.exe /text
```

L'exemple précédent peut comporter plusieurs méthodes nommées `MyMethod` avec différentes signatures. La commande suivante désassemble la méthode d’instance `MyMethod` avec le type de retour **void** et les types de paramètres **int32** et **string**.

```console
ildasm /item:"MyClass::MyMethod(instance void(int32,string)" MyFile.exe /text
```

> [!NOTE]
> Dans les versions 1.0 et 1.1 du .NET Framework, la parenthèse gauche qui suit le nom de la méthode doit être accompagnée d'une parenthèse droite après la signature : `MyMethod(instance void(int32))`. Dans la version 2.0 du .NET Framework, la parenthèse de fermeture doit être supprimée : `MyMethod(instance void(int32)`.

Pour récupérer une méthode `static` (méthode `Shared` dans Visual Basic), supprimez le mot clé `instance`. Les types de classes qui ne sont pas des types primitifs comme `int32` et `string` doivent inclure l'espace de noms et être précédés du mot clé `class`. Les types externes doivent être précédés du nom de la bibliothèque entre crochets. La commande suivante désassemble une méthode statique nommée `MyMethod` qui comprend un paramètre de type <xref:System.AppDomain> et un type de retour <xref:System.AppDomain>.

```console
ildasm /item:"MyClass::MyMethod(class [mscorlib]System.AppDomain(class [mscorlib]System.AppDomain)" MyFile.exe /text
```

Un type imbriqué doit être précédé de la classe le contenant, délimitée par une barre oblique. Par exemple, si la classe `MyNamespace.MyClass` contient une classe imbriquée nommée `NestedClass`, la classe imbriquée est identifiée comme suit : `class MyNamespace.MyClass/NestedClass`.

## <a name="see-also"></a>Voir aussi

- [Outils](../../../docs/framework/tools/index.md)
- [Ilasm.exe (assembleur IL)](../../../docs/framework/tools/ilasm-exe-il-assembler.md)
- [Processus d'exécution managée](../../../docs/standard/managed-execution-process.md)
- [Invites de commandes](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
