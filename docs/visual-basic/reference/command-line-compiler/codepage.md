---
title: -codepage
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: 34dbf36cc79a8c4715cf6a07c57d559e14f40030
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363628"
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
|`id`|Obligatoire. Le compilateur utilise la page de codes spécifiée par `id` pour interpréter l’encodage des fichiers sources.|  
  
## <a name="remarks"></a>Notes  
 Pour compiler le code source enregistré avec un encodage spécifique, vous pouvez utiliser `-codepage` pour spécifier la page de codes à utiliser. L' `-codepage` option s’applique à tous les fichiers de code source de votre compilation. Pour plus d’informations, consultez [encodage de caractères dans le .NET Framework](../../../standard/base-types/character-encoding.md).  
  
 L' `-codepage` option n’est pas nécessaire si les fichiers de code source ont été enregistrés à l’aide de la page de codes ANSI actuelle, Unicode ou UTF-8 avec une signature. Visual Studio enregistre par défaut tous les fichiers de code source avec la page de codes ANSI actuelle, à moins que l’utilisateur spécifie un autre encodage dans la boîte de dialogue **encodage** . Visual Studio utilise la boîte de dialogue **encodage** pour ouvrir des fichiers de code source enregistrés avec une page de codes différente.  
  
> [!NOTE]
> L' `-codepage` option n’est pas disponible dans l’environnement de développement Visual Studio ; elle est disponible uniquement lors de la compilation à partir de la ligne de commande.  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](index.md)
