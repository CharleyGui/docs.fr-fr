---
title: -nostdlib (Options du compilateur C#)
ms.date: 12/20/2019
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: ad8a2b5fc87dd7beee86d96331cf3961315be533
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345077"
---
# <a name="-nostdlib-c-compiler-options"></a>-nostdlib (Options du compilateur C#)

**-nostdlib** empêche l’importation du fichier mscorlib.dll, qui définit l’espace de noms System tout entier.

## <a name="syntax"></a>Syntaxe

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a>Notes 

Utilisez cette option si vous souhaitez définir ou créer vos propres objets et espace de noms System.

Si vous ne spécifiez pas **-nostdlib**, mscorlib.dll est importé dans votre programme (ce qui équivaut à spécifier **-nostdlib-**). Les options **-nostdlib** et **-nostdlib+** sont équivalentes.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Pour définir cette option de compilateur dans Visual Studio

> [!NOTE]
> Les instructions suivantes s’appliquent uniquement à Visual Studio 2015 (et versions antérieures). Le **Ne pas référence mscorlib.dll** construire la propriété n’existe pas dans les versions plus nouvelles de Visual Studio.

1. Ouvrez la page **Propriétés** du projet.

2. Cliquez sur la page de propriétés **Générer** .

3. Cliquez sur le bouton **Avancé**.

4. Modifiez la propriété **Ne pas référencer mscorlib.dll** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.

## <a name="see-also"></a>Voir aussi

- [Options de compilateur C](./index.md)
