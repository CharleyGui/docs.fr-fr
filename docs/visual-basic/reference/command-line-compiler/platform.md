---
title: -platform (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
ms.openlocfilehash: eb5513c6d8e4085e1b3f69de1d36a007fa27271e
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380311"
---
# <a name="-platform-visual-basic"></a>-platform (Visual Basic)
Spécifie la version de plateforme du CLR (Common Language Runtime) qui peut exécuter le fichier de sortie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`x86`|Compile votre assembly pour qu'il soit exécuté par le CLR 32 bits x86.|  
|`x64`|Compile votre assembly pour qu'il soit exécuté par le CLR 64 bits sur un ordinateur qui prend en charge le jeu d'instructions AMD64 ou EM64T.|  
|`Itanium`|Compile votre assembly pour qu'il soit exécuté par le CLR 64 bits sur un ordinateur doté d'un processeur Itanium.|  
|`arm`|Compile votre assembly pour qu'il s'exécute sur un ordinateur doté d'un processeur ARM (Advanced RISC Machine).|  
|`anycpu`|Compile votre assembly pour qu'il s'exécute sur n'importe quelle plateforme. L'application s'exécutera en tant qu'application 32 bits sur les versions 32 bits de Windows et en tant qu'application 64 bits sur les versions 64 bits de Windows. Cet indicateur est la valeur par défaut.|  
|`anycpu32bitpreferred`|Compile votre assembly pour qu'il s'exécute sur n'importe quelle plateforme. L'application s'exécutera en tant qu'application 32 bits sur les versions 32 et 64 bits de Windows. Cet indicateur est valide uniquement pour les fichiers exécutables (. (EXE) et nécessite .NET Framework 4.5.|  
  
## <a name="remarks"></a>Notes  
 Utilisez l'option `-platform` pour spécifier le type de processeur ciblé par le fichier de sortie.  
  
 En général, les assemblys .NET Framework écrits en Visual Basic s'exécutent de la même façon, quelle que soit la plateforme. Cependant, dans certains cas, leur comportement peut varier d'une plateforme à une autre. Voici les cas les plus courants :  
  
- Structures contenant des membres qui changent de taille selon la plateforme, comme un type pointeur.  
  
- Opération arithmétique de pointeur qui inclut des tailles constantes.  
  
- Appel de plateforme incorrect ou déclarations COM qui utilisent `Integer` pour des handles au lieu de <xref:System.IntPtr>.  
  
- Cast de <xref:System.IntPtr> en `Integer`.  
  
- Utilisation d'un appel de plateforme ou de COM interop avec des composants qui n'existent pas sur toutes les plateformes.  
  
 Le **-plateforme** option atténuera certains problèmes si vous savez que vous avez fait des hypothèses sur l’architecture de votre code s’exécutera sur. Plus précisément :  
  
- Si vous décidez de cibler une plateforme 64 bits et que l'application est exécutée sur un ordinateur 32 bits, le message d'erreur intervient bien plus tôt et est davantage axé sur le problème que sur l'erreur qui se produit quand ce commutateur n'est pas utilisé.  
  
- Si vous définissez l'indicateur `x86` au niveau de l'option et que l'application est par la suite exécutée sur un ordinateur 64 bits, l'application s'exécutera dans le sous-système WOW au lieu de s'exécuter en mode natif.  
  
 Sur un système d'exploitation Windows 64 bits :  
  
- Les assemblys compilés avec `-platform:x86` s'exécutent sur le CLR 32 bits fonctionnant sous WOW64.  
  
- Les fichiers exécutables compilés avec `-platform:anycpu` s'exécutent sur le CLR 64 bits.  
  
- Une DLL compilée avec `-platform:anycpu` s'exécute sur le même CLR que le processus dans lequel elle est chargée.  
  
- Les fichiers exécutables compilés avec `-platform:anycpu32bitpreferred` s'exécutent sur le CLR 32 bits.  
  
 Pour plus d’informations sur la façon de développer une application à exécuter sur une version 64 bits de Windows, consultez [Applications 64 bits](../../../framework/64-bit-apps.md).  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a>Définir - plateforme dans l’IDE Visual Studio  
  
1. Dans **l’Explorateur de solutions**, choisissez le projet, ouvrez le **projet** menu, puis sur **propriétés**.  
  
2. Sur le **compiler** onglet, activez ou désactivez le **préférer 32 bits** case à cocher, ou, dans le **unité centrale cible** , choisissez une valeur.  
  
     Pour plus d’informations, consultez [Page Compiler, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant montre comment utiliser l'option de compilateur `-platform`.  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a>Voir aussi

- [/target (Visual Basic)](target.md)
- [Compilateur de ligne de commande de Visual Basic](index.md)
- [Exemples de lignes de commande de compilation](sample-compilation-command-lines.md)
