---
title: Validation de la complexité des mots de passe
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: 9597d7a9d6b68b8c91f32d97da3532f181585cf6
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072351"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a>Procédure pas à pas : validation de la complexité des mots de passe (Visual Basic)

Cette méthode vérifie certaines caractéristiques de mot de passe fort et met à jour un paramètre de chaîne avec des informations sur la vérification de l’échec du mot de passe.  
  
 Les mots de passe peuvent être utilisés dans un système sécurisé pour autoriser un utilisateur. Toutefois, les mots de passe doivent être difficiles à deviner pour les utilisateurs non autorisés. Les attaquants peuvent utiliser un programme d' *attaque par dictionnaire* , qui itère au sein de tous les mots d’un dictionnaire (ou de plusieurs dictionnaires dans différentes langues) et teste si l’un des mots fonctionne en tant que mot de passe d’un utilisateur. Des mots de passe faibles, tels que « Yankees » ou « Mustang », peuvent être devinés rapidement. Des mots de passe plus forts, tels que « ? « L1N3vaFiNdMeyeP@sSWerd ! » Sont très moins susceptibles d’être devinés. Un système protégé par mot de passe doit s’assurer que les utilisateurs choisissent des mots de passe forts.  
  
 Un mot de passe fort est complexe (contenant un mélange de majuscules, de minuscules, de chiffres et de caractères spéciaux) et n’est pas un mot. Cet exemple montre comment vérifier la complexité.  
  
## <a name="example"></a>Exemple  
  
### <a name="code"></a>Code  

 [!code-vb[VbVbcnRegEx#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a>Compiler le code  

 Appelez cette méthode en passant la chaîne qui contient ce mot de passe.  
  
 Cet exemple nécessite :  
  
- Un accès aux membres de l’espace de noms <xref:System.Text.RegularExpressions>. Ajoutez une instruction `Imports` si vous n’utilisez pas de noms de membres qualifiés complets dans votre code. Pour plus d’informations, consultez [Instruction Imports (espace de noms et type .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="security"></a>Sécurité  

 Si vous déplacez le mot de passe sur un réseau, vous devez utiliser une méthode sécurisée pour le transfert des données. Pour plus d’informations, consultez [sécurité des applications Web ASP.net](/previous-versions/aspnet/330a99hc(v=vs.100)).
  
 Vous pouvez améliorer la précision de la `ValidatePassword` fonction en ajoutant des vérifications de complexité supplémentaires :  
  
- Comparez le mot de passe et ses sous-chaînes avec le nom de l’utilisateur, l’identificateur de l’utilisateur et un dictionnaire défini par l’application. En outre, traitez les caractères similaires visuellement comme équivalents lors de l’exécution des comparaisons. Par exemple, considérez les lettres « l » et « e » comme équivalentes aux chiffres « 1 » et « 3 ».  
  
- S’il n’y a qu’un seul caractère majuscule, assurez-vous qu’il ne s’agit pas du premier caractère du mot de passe.  
  
- Assurez-vous que les deux derniers caractères du mot de passe sont des caractères alphabétiques.  
  
- N’autorisez pas les mots de passe dans lesquels tous les symboles sont entrés à partir de la ligne supérieure du clavier.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Text.RegularExpressions.Regex>
- [Sécurité des applications web ASP.NET](/previous-versions/aspnet/330a99hc(v=vs.100))
