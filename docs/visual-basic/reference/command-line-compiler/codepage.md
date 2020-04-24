---
title: -codepage
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: a38fb4be9347b3372b4a459fce2e96b9e38c3a51
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343547"
---
# <a name="-codepage-visual-basic"></a>-CodePage (Visual Basic)
Spécifie la page de codes à utiliser pour tous les fichiers de code source inclus dans la compilation.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`id`|Obligatoire. Le compilateur utilise la page de codes spécifiée `id` par pour interpréter l’encodage des fichiers sources.|  
  
## <a name="remarks"></a>Notes  
 Pour compiler le code source enregistré avec un encodage spécifique, vous `-codepage` pouvez utiliser pour spécifier la page de codes à utiliser. L' `-codepage` option s’applique à tous les fichiers de code source de votre compilation. Pour plus d’informations, consultez [encodage de caractères dans le .NET Framework](../../../standard/base-types/character-encoding.md).  
  
 L' `-codepage` option n’est pas nécessaire si les fichiers de code source ont été enregistrés à l’aide de la page de codes ANSI actuelle, Unicode ou UTF-8 avec une signature. Visual Studio enregistre par défaut tous les fichiers de code source avec la page de codes ANSI actuelle, à moins que l’utilisateur spécifie un autre encodage dans la boîte de dialogue **encodage** . Visual Studio utilise la boîte de dialogue **encodage** pour ouvrir des fichiers de code source enregistrés avec une page de codes différente.  
  
> [!NOTE]
> L' `-codepage` option n’est pas disponible dans l’environnement de développement Visual Studio. elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
