---
title: Regasm.exe (outil Assembly Registration Tool)
ms.date: 03/30/2017
helpviewer_keywords:
- Assembly Registration tool
- assemblies [.NET Framework], registering
- Regasm.exe
- registering assemblies
ms.assetid: e190e342-36ef-4651-a0b4-0e8c2c0281cb
ms.openlocfilehash: 5eeed43f3d60bd5e443226a16963557546d81e7c
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635415"
---
# <a name="regasmexe-assembly-registration-tool"></a>Regasm.exe (outil Assembly Registration Tool)

L'outil Assembly Registration Tool (Inscription de l'assembly) lit les métadonnées figurant dans un assembly et ajoute les entrées nécessaires au Registre, ce qui permet aux clients COM de créer en toute transparence des classes .NET Framework. Une fois qu'une classe est inscrite, tout client COM peut l'utiliser comme s'il s'agissait d'une classe COM. La classe fait l'objet d'une seule inscription, lors de l'installation de l'assembly. Les instances des classes figurant dans l'assembly ne peuvent pas être créées à partir de COM tant qu'elles n'ont pas été concrètement inscrites.

Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio. Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).

À l'invite de commandes, tapez :

## <a name="syntax"></a>Syntaxe

```console
regasm assemblyFile [options]
```

## <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*assemblyFile*|Assembly à inscrire avec COM.|

|Option|Description|
|------------|-----------------|
|**/base de code**|Crée une entrée Codebase dans le Registre. L’entrée Codebase spécifie le chemin de fichier d’un assemblage qui n’est pas installé dans le cache d’assemblage global. Ne spécifiez pas cette option si vous installez par la suite l’assemblage que vous enregistrez dans le cache d’assemblage global. L’argument *assemblyFile* que vous spécifiez avec l’option **/codebase** doit être un [assembly avec nom fort](../../standard/assembly/strong-named.md).|
|**/enregistré**|Spécifie que cet outil fera uniquement référence aux bibliothèques de types qui ont déjà été inscrites.|
|**/asmpath:directory**|Spécifie un répertoire contenant des références d'assembly. Doit être utilisé avec l’option **/regfile**.|
|**/nologo**|Supprime l'affichage de la bannière de démarrage Microsoft.|
|**/regfile** [**:** *regFile*]|Génère le fichier .reg spécifié pour l'assembly, qui comporte les entrées du Registre nécessaires. La spécification de cette option ne modifie pas le Registre. Vous ne pouvez pas utiliser cette option avec les options **/u** ou **/tlb**.|
|**/silent** ou **/s**|Supprime l'affichage des messages indiquant la réussite des opérations.|
|**/tlb** [**:** *typeLibFile*]|Génère, à partir de l'assembly spécifié, une bibliothèque de types comportant les définitions des types accessibles définis dans l'assembly.|
|**/unregister** ou **/u**|Annule l’inscription des classes pouvant être créées figurant dans *assemblyFile*. Si cette option n'est pas spécifiée, Regasm.exe inscrit les classes pouvant être créées dans l'assembly.|
|**/verbose**|Spécifie le mode détaillé ; affiche la liste de tous les assemblys référencés pour lesquels une bibliothèque de types doit être générée, en cas de spécification avec l’option **/tlb**.|
|**/?** ou **/help**|Affiche la syntaxe et les options de commande de l'outil.|

> [!NOTE]
> Les options de ligne de commande de Regasm.exe ne respectent pas la casse. Il vous suffit d'indiquer les éléments de l'option nécessaires à son identification de manière unique. Par exemple, **/n** équivaut à **/nologo**, et **/t:** *outfile.tlb* à **/tlb:** *outfile.tlb*.

## <a name="remarks"></a>Notes

Vous pouvez utiliser l’option **/regfile** pour générer un fichier .reg comportant les entrées du Registre plutôt que d’apporter directement les modifications au Registre. Vous pouvez mettre à jour le Registre d'un ordinateur en important le fichier .reg à l'aide de l'Éditeur du Registre (Regedit.exe). Le fichier .reg ne contient aucune mise à jour du registre qui peut être faite par des fonctions de registre définies par l’utilisateur. **L’option /regfile** n’émet que des entrées de registre pour les classes gérées. Cette option n'émet pas d'entrée pour `TypeLibID` ou `InterfaceID`.

Quand vous spécifiez l’option **/tlb**, Regasm.exe génère et inscrit une bibliothèque de types décrivant les types figurant dans l’assembly. Regasm.exe place les bibliothèques de types générées dans le répertoire de travail en cours ou dans le répertoire spécifié pour le fichier de sortie. La génération d'une bibliothèque de types pour un assembly référençant d'autres assemblys peut provoquer la génération de plusieurs bibliothèques de types en une seule opération. Vous pouvez utiliser la bibliothèque de types pour fournir les informations de type aux outils de développement comme Visual Studio. N’utilisez pas l’option **/tlb** si l’assemblage que vous enregistrez a été produit par l’importateur de bibliothèque de type ([Tlbimp.exe](tlbimp-exe-type-library-importer.md)). Vous ne pouvez pas exporter de bibliothèque de types à partir d'un assembly ayant été importé depuis une bibliothèque de types. L’option **/tlb** produit le même effet que l’exportateur de bibliothèques de types ([Tlbexp.exe](tlbexp-exe-type-library-exporter.md)) et Regasm.exe, à l’exception près que Tlbexp.exe n’inscrit pas la bibliothèque de types qu’il génère.  Si vous utilisez l’option **/tlb** pour enregistrer une bibliothèque de type, vous pouvez utiliser l’option **/tlb** avec l’option **/unregister** pour déenregistrer la bibliothèque de type. L'utilisation simultanée des deux options annulera l'inscription de la bibliothèque de types et des entrées d'interface, ce qui peut considérablement nettoyer le Registre.

Lorsque vous inscrivez un assembly destiné à être utilisé par COM, Regasm.exe ajoute des entrées au Registre sur l'ordinateur local. Plus précisément, il crée des clés de Registre dépendantes de la version qui permettent à plusieurs versions du même assembly de s'exécuter côte-à-côte sur un ordinateur. La première fois qu’un assemblage est enregistré, une clé de haut niveau est créée pour l’assemblage, et un sous-clé unique est créé pour la version spécifique. Chaque fois que vous inscrivez une nouvelle version de l'assembly, Regasm.exe crée une sous-clé pour la nouvelle version.

Par exemple, imaginons un scénario dans lequel vous inscrivez le composant managé, myComp.dll, version 1.0.0.0 pour qu'il soit utilisé par COM. Par la suite, vous inscrivez myComp.dll, version 2.0.0.0. Vous décidez que toutes les applications clientes COM sur l'ordinateur utilisent myComp.dll version 2.0.0.0 et vous décidez d'annuler l'inscription de myComponent.dll version 1.0.0.0. Ce modèle de Registre vous permet d'annuler l'inscription de myComp.dll version 1.0.0.0, car seule la sous-clé de la version 1.0.0.0 est supprimée.

Après avoir inscrit un assembly à l’aide de Regasm.exe, vous pouvez l’installer dans le [Global Assembly Cache](../app-domains/gac.md), pour qu’il puisse être activé à partir d’un client COM. Si l'assembly ne va être activé que par une seule application, vous pouvez alors le placer dans le répertoire de cette application.

## <a name="examples"></a>Exemples

La commande suivante inscrit toutes les classes publiques figurant dans `myTest.dll`.

```console
regasm myTest.dll
```

La commande suivante génère le fichier `myTest.reg`, qui comporte toutes les entrées du Registre nécessaires. Cette commande ne met pas à jour le Registre.

```console
regasm myTest.dll /regfile:myTest.reg
```

La commande suivante inscrit toutes les classes publiques figurant dans `myTest.dll` et elle génère et inscrit la bibliothèque de types `myTest.tlb`, qui comporte les définitions de tous les types publics définis dans `myTest.dll`.

```console
regasm myTest.dll /tlb:myTest.tlb
```

## <a name="see-also"></a>Voir aussi

- [Outils](index.md)
- [Tlbexp.exe (Type Library Exporter)](tlbexp-exe-type-library-exporter.md)
- [Tlbimp.exe (Importateur de bibliothèque de type)](tlbimp-exe-type-library-importer.md)
- [Inscription d’assemblys dans COM](../interop/registering-assemblies-with-com.md)
- [Invite de commande](developer-command-prompt-for-vs.md)
