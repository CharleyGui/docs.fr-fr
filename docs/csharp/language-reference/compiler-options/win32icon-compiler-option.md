---
description: -win32icon (Options du compilateur C#)
title: -win32icon (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: 5b62bbfe28bb5aa82605a88a83cf82eff9278807
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168866"
---
# <a name="-win32icon-c-compiler-options"></a>-win32icon (Options du compilateur C#)

L’option **-win32icon** insère un fichier .ico dans le fichier de sortie, ce qui lui donne l’apparence souhaitée dans l’Explorateur de fichiers.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a>Arguments  

 `filename`  
 Fichier .ico que vous voulez ajouter à votre fichier de sortie.  
  
## <a name="remarks"></a>Notes  

 Un fichier .ico peut être créé avec le [compilateur de ressources](/windows/desktop/menurc/resource-compiler). Le compilateur de ressources est appelé quand vous compilez un programme Visual C++ ; un fichier .ico est alors créé à partir du fichier .rc.  
  
 Consultez [-linkresource](./linkresource-compiler-option.md) pour référencer ou [-resource](./resource-compiler-option.md) pour attacher un fichier de ressources .NET Framework. Consultez [-win32res](./win32res-compiler-option.md) pour importer un fichier .res.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1. Ouvrez les pages **Propriétés** du projet.  
  
2. Cliquez sur la page de propriétés **Application**.  
  
3. Modifiez la propriété **Icône d’application**.  
  
 Pour plus d’informations sur la façon de définir cette option du compilateur par programmation, consultez <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.  
  
## <a name="example"></a>Exemple  

 Compilez `in.cs` et attachez un fichier .ico `rf.ico` afin de générer le fichier `in.exe` :  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a>Voir aussi

- [Options du compilateur C#](./index.md)
- [Gestion des propriétés des projets et des solutions](/visualstudio/ide/managing-project-and-solution-properties)
