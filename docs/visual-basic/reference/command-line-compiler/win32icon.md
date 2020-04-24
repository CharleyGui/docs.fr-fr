---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: 6b4b69d227c857442de6857fac023090b3698e81
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004635"
---
# <a name="-win32icon"></a>-win32icon
Insère un fichier. ico dans le fichier de sortie. Ce fichier. ico représente le fichier de sortie dans l' **Explorateur de fichiers**.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`filename`|Fichier. ico à ajouter à votre fichier de sortie. Placez le nom de fichier entre guillemets ("") s’il contient un espace.|  
  
## <a name="remarks"></a>Notes  
 Vous pouvez créer un fichier. ico avec le compilateur de ressources Microsoft Windows (RC). Le compilateur de ressources est appelé lorsque vous compilez un Visual C++ programme ; un fichier. ico est créé à partir du fichier. rc. Les options `-win32icon` et `-win32resource` s’excluent mutuellement.  
  
 Consultez [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) pour référencer un fichier de ressources .NET Framework, ou [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) pour attacher un fichier de ressources de .NET Framework. Consultez [-Win32Resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) pour importer un fichier. res.  
  
|Pour définir-win32icon dans l’IDE de Visual Studio|  
|---|  
|1. Sélectionnez un projet dans **Explorateur de solutions**. Dans le menu **Projet** , cliquez sur **Propriétés**. <br />2. cliquez sur l’onglet **application** .<br />3. modifiez la valeur dans la zone **icône** .|  
  
## <a name="example"></a>Exemple  
 Le code suivant compile `In.vb` et joint un fichier. ico,. `Rf.ico`  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
