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
ms.openlocfilehash: f23f8c48a31dffa7d350c872aed7505da7a36861
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73105056"
---
# <a name="ildasmexe-il-disassembler"></a>Ildasm.exe (Désassembleur IL)

Le Désassembleur IL est un outil associé à l'Assembleur IL (*Ilasm.exe*). *Ildasm.exe* crée, à partir d'un fichier exécutable portable (PE) contenant du code IL (intermediate language), un fichier texte pouvant servir d'entrée dans *Ilasm.exe*.

Cet outil est installé automatiquement avec Visual Studio. Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7). Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).

À l'invite de commandes, tapez :

## <a name="syntax"></a>Syntaxe

```console
ildasm [options] [PEfilename] [options]
```

## <a name="parameters"></a>Paramètres

Les options suivantes sont disponibles pour *.exe*, *.dll*, *.obj*, *.lib*, et *.winmd* fichiers.

| Option | Description |
| ------ | ----------- |
|**/out**`filename`|Crée un fichier de sortie avec le `filename` spécifié, au lieu d’afficher les résultats dans une interface graphique utilisateur.|
|**/rtf**|Produit la sortie au format RTF. Non valide avec l’option **/text**.|
|**/texte**|Affiche les résultats dans la fenêtre de console, plutôt que dans une interface graphique utilisateur ou dans un fichier de sortie.|
|**/html**|Produit la sortie au format HTML. Valide avec l’option **/output** uniquement.|
|**/?**|Affiche la syntaxe de commande et les options de l'outil.|

Les options suivantes sont également disponibles pour les fichiers *.exe*, *.dll* et *.winmd*.

| Option | Description |
| ------ | ----------- |
|**/octets**|Affiche les octets actuels, au format hexadécimal, sous forme de commentaires d'instructions.|
|**/caverbal**|Produit des blobs d'attribut personnalisés sous forme verbale. La valeur par défaut est la forme binaire.|
|**/linenum**|Inclut des références dans les lignes sources d'origine.|
|**/nobar**|Supprime la fenêtre pop-up de l'indicateur de progression du code machine.|
|**/noca**|Supprime la sortie d'attributs personnalisés.|
|**/projet**|Affiche les métadonnées telles qu'elles apparaissent dans le code managé, plutôt que telles qu'elles apparaissent dans le Windows Runtime natif. Si `PEfilename` n'est pas un fichier de métadonnées Windows (*.winmd*), cette option n'a aucun effet. Consultez [Prise en charge .NET Framework pour les applications Windows Store et Windows Runtime](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).|
|**/pubonly**|Désassemble uniquement les membres et les types publics. Équivaut à **/visibility:PUB**.|
|**/quoteallnames**|Entoure tous les noms de guillemets simples.|
|**/raweh**|Affiche les clauses de gestion des exceptions sous une forme brute.|
|**/source**|Affiche les lignes sources d'origine sous forme de commentaires.|
|**/jetons**|Affiche les jetons de métadonnées des classes et des membres.|
|**/visibility:** `vis`[+`vis`...]|Désassemble uniquement les types ou les membres avec la visibilité spécifiée. Les valeurs valides pour `vis` sont les suivantes :<br /><br /> **PUB** — Public<br /><br /> **PRI** — Privé<br /><br /> **FAM** — Famille<br /><br /> **ASM** — Assembly<br /><br /> **FAA** — Famille et Assembly<br /><br /> **FOA** — Famille ou Assembly<br /><br /> **PSC** — Portée privée<br /><br /> Pour obtenir des définitions de ces modificateurs de visibilité, consultez <xref:System.Reflection.MethodAttributes> et <xref:System.Reflection.TypeAttributes>.|

Les options suivantes sont valables pour *.exe*, *.dll*, et *.winmd* fichiers pour la sortie de fichier ou de console seulement.

| Option | Description |
| ------ | ----------- |
|**/all**|Spécifie une combinaison des options **/header**, **/bytes**, **/stats**, **/classlist** et **/tokens**.|
|**/classlist**|Inclut une liste de classes définie dans le module.|
|**/en avant**|Utilise la déclaration de classe anticipée.|
|**/en-têtes**|Inclut les informations d'en-tête du fichier dans la sortie.|
|**/article:** `class`[**::** `member`[`(sig`]|Désassemble les éléments suivants en fonction de l’argument fourni :<br /><br /> -   Désassemble la `class` spécifiée.<br />-   Désassemble le `member` spécifié de la `class`.<br />-   Désassemble le `member` de la `class` avec la signature spécifiée `sig`. Le format de `sig` est le suivant :<br />     [`instance`] `returnType`(`parameterType1`, `parameterType2`, …, `parameterTypeN`)<br />     **Note** Dans les versions .NET Framework 1.0 et `sig` 1.1, doit `(sig)`être suivie d’une parenthèse de clôture: . À compter de .NET Framework 2.0, la parenthèse fermante doit être omise : `(sig`.|
|**/noil**|Supprime la sortie du code d'assembly IL.|
|**/stats**|Inclut des statistiques sur l'image.|
|**/typelist**|Produit la liste complète des types afin de conserver le classement des types dans un aller-retour.|
|**/unicode**|Utilise l'encodage Unicode pour la sortie.|
|**/utf8**|Utilise l'encodage UTF-8 pour la sortie. ANSI est la valeur par défaut.|

Les options suivantes sont valables pour *.exe*, *.dll*, *.obj*, *.lib*, et *.winmd* fichiers pour le fichier ou la sortie de console seulement.

| Option | Description |
| ------ | ----------- |
|**/métadonnées**`specifier`[MD ]|Affiche les métadonnées, où `specifier` est :<br /><br /> **MDHEADER** — Affiche les informations d’en-tête et de taille des métadonnées.<br /><br /> **HEX** — Affiche les informations en hexadécimales ainsi qu’en mots.<br /><br /> **CSV** — Affiche les nombres d’enregistrements et les tailles de tas.<br /><br /> **UNREX** — Affiche les externes non résolus.<br /><br /> **SCHEMA** — Affiche les informations relatives au schéma et à l’en-tête des métadonnées.<br /><br /> **RAW** — Affiche les tables de métadonnées brutes.<br /><br /> **HEAPS** — Affiche les tas bruts.<br /><br /> **VALIDATE** — Valide la cohérence des métadonnées.<br /><br /> Vous pouvez spécifier plusieurs fois **/metadata**, avec des valeurs différentes pour `specifier`.|

Les options suivantes sont valables pour les fichiers *.lib* pour la sortie de fichier ou de console seulement.

| Option | Description |
| ------ | ----------- |
|**/objectfile**=`filename`|Affiche les métadonnées d'un fichier objet seul dans la bibliothèque spécifiée.|

> [!NOTE]
> Aucune option d’*Ildasm.exe* ne respecte pas la casse et toutes sont reconnues à leurs trois premières lettres. Par exemple, **/quo** est équivalent à **/quoteallnames**. Les options spécifiant des arguments prennent en charge les deux-points (:) ou le signe égal (=) en tant que séparateur entre l'option et l'argument. Par exemple, **/output:** *filename* équivaut à **/output=** *filename*.

## <a name="remarks"></a>Notes 

*Ildasm.exe* ne fonctionne que sur les fichiers PE sur disque. Il ne fonctionne pas avec des fichiers installés dans le Global Assembly Cache.

Le fichier texte généré par *Ildasm.exe* peut servir d'entrée dans l'Assembleur IL (*Ilasm.exe*). Cet outil s'avère, par exemple, utile lors de la compilation d'un code dans un langage de programmation ne prenant pas en charge tous les attributs de métadonnées du runtime. Après avoir compilé le code et l’exécution de sa sortie à travers *Ildasm.exe*, le fichier texte IL résultant peut être modifié à la main pour ajouter les attributs manquants. Vous pouvez ensuite exécuter ce fichier texte via l'Assembleur IL pour générer un fichier exécutable final.

> [!NOTE]
> Actuellement, vous ne pouvez pas utiliser cette technique avec des fichiers exécutables portables qui contiennent du code natif incorporé (par exemple, des fichiers exécutables portables générés par Visual C++).  

Vous pouvez utiliser l’interface graphique utilisateur par défaut du Désassembleur IL pour afficher, sous forme d’arborescence, le code désassemblé et les métadonnées de tout fichier exécutable portable existant. Pour utiliser l’interface graphique utilisateur, tapez **ildasm** au niveau de la ligne de commande sans préciser l’argument *PEfilename* ni d’options. Du menu **Fichier,** vous pouvez naviguer vers le fichier PE que vous souhaitez charger dans *Ildasm.exe*. Pour enregistrer les métadonnées et le code désassemblé affichés pour le PE sélectionné, sélectionnez la commande **Dump** dans le menu **Fichier**. Pour enregistrer uniquement l’affichage d’arborescence hiérarchique, sélectionnez la commande **Dump de l’arborescence** dans le menu **Fichier**. Pour plus d’informations sur le chargement d’un fichier dans *Ildasm.exe* et l’interprétation de la sortie, consultez le tutoriel *Ildasm.exe*, qui se trouve dans le dossier Samples fourni avec le SDK Windows.

Si vous *fournissez à Ildasm.exe* un argument *PEfilename* qui contient des ressources intégrées, l’outil produit plusieurs fichiers de sortie : un fichier texte qui contient du code IL et, pour chaque ressource gérée intégrée, un fichier .ressources produite à partir du nom de la ressource à partir de métadonnées. Si une ressource non managée est incorporée dans *PEfilename*, un fichier .res est généré à l’aide du nom de fichier spécifié pour la sortie IL par l’option **/output**.

> [!NOTE]
> *Ildasm.exe* ne montre que des descriptions de métadonnées pour les fichiers *d’entrée .obj* et *.lib.* Le code IL de ces types de fichiers n'est pas désassemblé.

Vous pouvez exécuter *Ildasm.exe* sur un fichier an.exe ou *.dll* pour déterminer si le fichier est géré. Si le fichier n'est pas managé, l'outil affiche un message indiquant que le fichier ne contient pas d'en-tête du Common Language Runtime valide et qu'il ne peut pas être désassemblé. S'il s'agit d'un fichier managé, l'outil s'exécute correctement.

## <a name="version-information"></a>Informations sur la version

À compter de .NET Framework 4.5, *Ildasm.exe* gère un objet blob (Binary Large Object) marshal non reconnu en affichant le contenu binaire brut. Par exemple, le code suivant montre comment un BLOB marshal généré par un programme C# s'affiche :

```csharp
public void Test([MarshalAs((short)70)] int test) { }
```

```il
// IL from Ildasm.exe output
.method public hidebysig instance void Test(int32  marshal({ 46 }) test) cil managed
```

À compter de .NET Framework 4.5, *Ildasm.exe* affiche les attributs qui sont appliqués aux implémentations d’interfaces, comme indiqué dans l’extrait suivant de la sortie du fichier *Ildasm.exe* :

```il
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

La commande suivante provoque l’affichage des métadonnées `MyHello.exe` et du code démonté du fichier PE dans l’interface graphique par défaut *d’Ildasm.exe.*

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

Si le fichier `MyApp.exe` contient des ressources managées et non managées incorporées, la commande suivante génère quatre fichiers : *MyApp.il*, *MyApp.res*, *Icons.resources* et *Message.resources* :

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

- [Outils](index.md)
- [Ilasm.exe (Assembleur IL)](ilasm-exe-il-assembler.md)
- [Processus d'exécution managée](../../standard/managed-execution-process.md)
- [Invites de commandes](developer-command-prompt-for-vs.md)
