---
title: -debug
ms.date: 03/10/2018
helpviewer_keywords:
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
ms.openlocfilehash: df65d1c095f5a22d562d78e15baf750a20ec2556
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716772"
---
# <a name="-debug-visual-basic"></a>-Debug (Visual Basic)

Fait en sorte que le compilateur génère des informations de débogage et les place dans le ou les fichiers de sortie.

## <a name="syntax"></a>Syntaxe

```console
-debug[+ | -]
```

ou

```console
-debug:[full | pdbonly]
```

## <a name="arguments"></a>Arguments

|Terme|Définition|
|---|---|
|`+` &#124; `-`|Facultatif. Si `+` vous `-debug` spécifiez ou, le compilateur génère des informations de débogage et les place dans un fichier. pdb. La `-` spécification de a le même effet que `-debug`la non-spécification de.|
|`full` &#124; `pdbonly`|Facultatif. Indique le type d'informations de débogage générées par le compilateur. Si vous ne spécifiez `-debug:pdbonly`pas, la valeur `full`par défaut est, ce qui vous permet d’attacher un débogueur au programme en cours d’exécution. L' `pdbonly` argument autorise le débogage du code source lorsque le programme est démarré dans le débogueur, mais il affiche le code en langage assembleur uniquement lorsque le programme en cours d’exécution est attaché au débogueur.|

## <a name="remarks"></a>Notes

Utilisez cette option pour créer des versions Debug. Si vous ne spécifiez `-debug`pas `-debug+`, ou `-debug:full`, vous ne pourrez pas déboguer le fichier de sortie de votre programme.

Par défaut, les informations de débogage ne sont pas émises (`-debug-`). Pour émettre des informations de débogage, `-debug` spécifiez ou `-debug+`.

Pour plus d’informations sur la configuration des performances de débogage d’une application, consultez [Simplification du débogage d’une image](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).

|Pour définir-Debug dans l’environnement de développement intégré de Visual Studio|
|---|
|1. quand un projet est sélectionné dans **Explorateur de solutions**, dans le menu **projet** , cliquez sur **Propriétés**. <br />2. cliquez sur l’onglet **compiler** .<br />3. cliquez sur **Options avancées de compilation**.<br />4. modifiez la valeur dans la zone **générer des informations de débogage** .|

## <a name="example"></a>Exemple

L’exemple suivant place des informations de débogage dans le `App.exe`fichier de sortie.

```console
vbc -debug -out:app.exe test.vb
```

## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
