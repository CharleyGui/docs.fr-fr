---
title: Conventions de codage
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- examples [Visual Basic], coding conventions
- Visual Basic code, conventions
ms.assetid: c1df130b-fec6-49a5-becf-0a7e494a1d0f
ms.openlocfilehash: eae283c757ddeb1290c15d82a41c8028a8941e63
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "91059156"
---
# <a name="visual-basic-coding-conventions"></a>Conventions de codage Visual Basic

Microsoft développe des exemples et de la documentation qui suivent les instructions de cette rubrique. Si vous suivez les mêmes conventions de codage, vous pouvez bénéficier des avantages suivants :  
  
- Votre code aura un aspect cohérent, afin que les lecteurs puissent mieux se concentrer sur le contenu, pas sur la disposition.  
  
- Les lecteurs comprennent votre code plus rapidement, car ils peuvent faire des hypothèses sur la base de l’expérience précédente.  
  
- Vous pouvez copier, modifier et gérer le code plus facilement.  
  
- Vous vous assurez que votre code illustre les « meilleures pratiques » pour Visual Basic.  
  
## <a name="naming-conventions"></a>Conventions d'affectation de noms  
  
- Pour plus d’informations sur les instructions d’affectation de noms, consultez la rubrique [règles d’affectation de noms](../../../standard/design-guidelines/naming-guidelines.md) .  
  
- N’utilisez pas « My » ou « My » dans le nom d’une variable. Cette pratique crée une confusion avec les `My` objets.  
  
- Vous n’avez pas besoin de modifier les noms des objets dans le code généré automatiquement pour qu’ils correspondent aux indications.  
  
## <a name="layout-conventions"></a>Conventions de disposition  
  
- Insérez des tabulations comme espaces et utilisez la mise en retrait intelligente avec des retraits à quatre espaces.  
  
- Utilisez une énumération simple (reformatage **) du code** pour reformater votre code dans l’éditeur de code. Pour plus d’informations, consultez [options, éditeur de texte, de base (Visual Basic)](/visualstudio/ide/reference/options-text-editor-basic-visual-basic).  
  
- Utilisez une seule instruction par ligne. N’utilisez pas le caractère de séparation de ligne Visual Basic ( :).  
  
- Évitez d’utiliser le caractère de continuation de ligne explicite « _ » en faveur de la continuation de ligne implicite partout où le langage l’autorise.  
  
- Utilisez une seule déclaration par ligne.  
  
- Si la **liste (reformatage) de code** ne met pas en forme les lignes de continuation de façon automatique, mettez en retrait manuellement les lignes de continuation d’un taquet de tabulation. Toutefois, aligner toujours les éléments à gauche dans une liste.  
  
    ```vb  
    a As Integer,  
    b As Integer  
    ```  
  
- Ajoutez au moins une ligne vide entre les définitions de méthode et de propriété.  
  
## <a name="commenting-conventions"></a>Conventions de commentaires  
  
- Placez les commentaires sur une ligne distincte plutôt qu’à la fin d’une ligne de code.  
  
- Commencez le texte de commentaire par une lettre majuscule, puis terminez le texte de commentaire par un point.  
  
- Insérez un espace entre le délimiteur de commentaire (') et le texte de commentaire.  
  
     [!code-vb[VbVbalrGuidelines#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#2)]  
  
- N’entourez pas les commentaires avec des blocs d’astérisques mis en forme.  
  
## <a name="program-structure"></a>Structure du programme  
  
- Lorsque vous utilisez la `Main` méthode, utilisez la construction par défaut pour les nouvelles applications console et utilisez `My` pour les arguments de ligne de commande.  
  
     [!code-vb[VbVbalrGuidelines#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#3)]  
  
## <a name="language-guidelines"></a>Directives du langage  
  
### <a name="string-data-type"></a>String, type de données  
  
- Utilisez une [interpolation de chaîne](../language-features/strings/interpolated-strings.md) pour concaténer les chaînes courtes, comme illustré dans le code suivant.
  
     ```vb
     MsgBox($"hello{vbCrLf}goodbye")
     ```
  
- Pour ajouter des chaînes dans des boucles, utilisez l' <xref:System.Text.StringBuilder> objet.  
  
     [!code-vb[VbVbalrGuidelines#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#5)]  
  
### <a name="relaxed-delegates-in-event-handlers"></a>Délégués souples dans les gestionnaires d’événements  

 Ne qualifiez pas explicitement les arguments (Object et EventArgs) aux gestionnaires d’événements. Si vous n’utilisez pas les arguments d’événement passés à un événement (par exemple, sender As Object, e As EventArgs), utilisez des délégués souples et ignorez les arguments d’événement dans votre code :  
  
 [!code-vb[VbVbalrGuidelines#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#7)]  
  
### <a name="unsigned-data-type"></a>Type de données non signé  
  
- Utilisez `Integer` plutôt que des types non signés, sauf s’ils sont nécessaires.  
  
### <a name="arrays"></a>Tableaux  
  
- Utilisez la syntaxe abrégée lorsque vous initialisez des tableaux sur la ligne de déclaration. Par exemple, utilisez la syntaxe suivante.  
  
     [!code-vb[VbVbalrGuidelines#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#8)]  
  
     N’utilisez pas la syntaxe suivante.  
  
     [!code-vb[VbVbalrGuidelines#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#9)]  
  
- Placez l’indicateur de tableau sur le type, et non sur la variable. Par exemple, utilisez la syntaxe suivante :  
  
     [!code-vb[VbVbalrGuidelines#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#11)]  
  
     N’utilisez pas la syntaxe suivante :  
  
     [!code-vb[VbVbalrGuidelines#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#10)]  
  
- Utilisez la syntaxe {} lorsque vous déclarez et initialisez des tableaux de types de données de base. Par exemple, utilisez la syntaxe suivante :  
  
     [!code-vb[VbVbalrGuidelines#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#12)]  
  
     N’utilisez pas la syntaxe suivante :  
  
     [!code-vb[VbVbalrGuidelines#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#13)]  
  
### <a name="use-the-with-keyword"></a>Utiliser le mot clé with  

 Lorsque vous effectuez une série d’appels à un objet, envisagez d’utiliser le `With` mot clé :  
  
 [!code-vb[VbVbalrGuidelines#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#15)]  
  
### <a name="use-the-trycatch-and-using-statements-when-you-use-exception-handling"></a>Utilisez le bloc try... Instructions catch et Using lorsque vous utilisez la gestion des exceptions  

 N’utilisez pas `On Error Goto`.  
  
### <a name="use-the-isnot-keyword"></a>Utiliser le mot clé IsNot  

 Utilisez le `IsNot` mot clé à la place de `Not...Is Nothing` .  
  
### <a name="new-keyword"></a>Mot clé New  
  
- Utilisez l’instanciation abrégée. Par exemple, utilisez la syntaxe suivante :  
  
     [!code-vb[VbVbalrGuidelines#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#21)]  
  
     La ligne précédente est équivalente à celle-ci :  
  
     [!code-vb[VbVbalrGuidelines#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#22)]  
  
- Utilisez les initialiseurs d’objets pour les nouveaux objets au lieu du constructeur sans paramètre :  
  
     [!code-vb[VbVbalrGuidelines#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#23)]  
  
### <a name="event-handling"></a>Gestion des événements  
  
- Utilisez `Handles` plutôt que `AddHandler` :  
  
     [!code-vb[VbVbalrGuidelines#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#24)]  
  
- Utilisez `AddressOf` et n’instanciez pas le délégué explicitement :  
  
     [!code-vb[VbVbalrGuidelines#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#25)]  
  
- Lorsque vous définissez un événement, utilisez la syntaxe abrégée et laissez le compilateur définir le délégué :  
  
     [!code-vb[VbVbalrGuidelines#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#26)]  
  
- Ne vérifiez pas si un événement est `Nothing` (null) avant d’appeler la `RaiseEvent` méthode. `RaiseEvent` vérifie `Nothing` avant de déclencher l’événement.  
  
### <a name="using-shared-members"></a>Utilisation de membres partagés  

 Appelez `Shared` les membres à l’aide du nom de la classe, et non d’une variable d’instance.  
  
### <a name="use-xml-literals"></a>Utiliser des littéraux XML  

 Les littéraux XML simplifient les tâches les plus courantes que vous rencontrez lorsque vous travaillez avec XML (par exemple, charger, interroger et transformer). Lorsque vous développez avec XML, suivez ces instructions :  
  
- Utilisez des littéraux XML pour créer des fragments et des documents XML au lieu d’appeler directement des API XML.  
  
- Importez des espaces de noms XML au niveau du fichier ou du projet pour tirer parti des optimisations des performances des littéraux XML.  
  
- Utilisez les propriétés d’axe XML pour accéder aux éléments et aux attributs dans un document XML.  
  
- Utilisez des expressions incorporées pour inclure des valeurs et créer du code XML à partir de valeurs existantes au lieu d’utiliser des appels d’API tels que la `Add` méthode :  
  
     [!code-vb[VbVbalrGuidelines#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#27)]  
  
### <a name="linq-queries"></a>Requêtes LINQ  
  
- Utilisez des noms explicites pour les variables de requête :  
  
     [!code-vb[VbVbalrGuidelines#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#28)]  
  
- Fournissez des noms pour les éléments d’une requête pour vous assurer que les noms de propriété des types anonymes sont correctement capitalisés à l’aide de la casse Pascal :  
  
     [!code-vb[VbVbalrGuidelines#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#29)]  
  
- Renommez les propriétés lorsque les noms de propriétés dans le résultat sont ambigus. Par exemple, si votre requête retourne un nom de client et un ID de commande, renommez-les au lieu de les laisser sous `Name` la forme et `ID` dans le résultat :  
  
     [!code-vb[VbVbalrGuidelines#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#30)]  
  
- Utilisez l’inférence de type dans la déclaration des variables de requête et des variables de portée :  
  
     [!code-vb[VbVbalrGuidelines#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#31)]  
  
- Alignez les clauses de requête sous l' `From` instruction :  
  
     [!code-vb[VbVbalrGuidelines#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#32)]  
  
- Utilisez `Where` les clauses avant les autres clauses de requête afin que les clauses de requête ultérieures fonctionnent sur l’ensemble de données filtré :  
  
     [!code-vb[VbVbalrGuidelines#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#33)]  
  
- Utilisez la `Join` clause pour définir explicitement une opération de jointure au lieu d’utiliser la `Where` clause pour définir implicitement une opération de jointure :  
  
     [!code-vb[VbVbalrGuidelines#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrGuidelines/VB/Class1.vb#34)]  
  
## <a name="see-also"></a>Voir aussi

- [Instructions de codage sécurisé](../../../standard/security/secure-coding-guidelines.md)
