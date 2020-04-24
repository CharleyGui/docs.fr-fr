---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: 91f2a27ed9b6fb296dbb9e50fc488fd012311890
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005507"
---
# <a name="-main"></a>-main
Spécifie la classe ou le module qui contient la procédure `Sub Main`.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-main:location  
```  
  
## <a name="arguments"></a>Arguments  
 `location`  
 Obligatoire. Nom de la classe ou du module qui contient la `Sub Main` procédure à appeler au démarrage du programme. Il peut s’agir de la forme **-main : module** ou **-main : namespace. module**.  
  
## <a name="remarks"></a>Notes  
 Utilisez cette option lorsque vous créez un fichier exécutable ou un programme exécutable Windows. Si l’option **-main** est omise, le compilateur recherche un partagé `Sub Main` valide dans toutes les classes et tous les modules publics.  
  
 Pour plus d’informations sur les différentes formes de la `Main` procédure, consultez la [procédure principale dans Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) .  
  
 Quand `location` est une classe qui hérite de <xref:System.Windows.Forms.Form>, le compilateur fournit une procédure `Main` par défaut qui démarre l’application si la classe n' `Main` a pas de procédure. Cela vous permet de compiler du code sur la ligne de commande qui a été créée dans l’environnement de développement.  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a>Pour définir-main dans l’environnement de développement intégré de Visual Studio  
  
1. Sélectionnez un projet dans l' **Explorateur de solutions**. Dans le menu **Projet** , cliquez sur **Propriétés**.  
  
2. Cliquez sur l’onglet **Application** .  
  
3. Vérifiez que la case à cocher **activer l’infrastructure** de l’application n’est pas activée.  
  
4. Modifiez la valeur dans la zone **objet de démarrage** .  
  
## <a name="example"></a>Exemple  
 Le code suivant `T2.vb` compile et `T3.vb`, en spécifiant que la `Sub Main` procédure sera trouvée dans la `Test2` classe.  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-cible (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Procédure Main dans Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
