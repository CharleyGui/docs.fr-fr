---
title: 'Comment : référencer les objets COM à partir de Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
ms.openlocfilehash: 43ba068663db9f8c3816a6f731395a6682a130e6
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91083291"
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a>Comment : référencer les objets COM à partir de Visual Basic

Dans Visual Basic, l’ajout de références à des objets COM qui ont des bibliothèques de types requiert la création d’un assembly d’interopérabilité pour la bibliothèque COM. Les références aux membres de l’objet COM sont routées vers l’assembly d’interopérabilité, puis transmises à l’objet COM réel. Les réponses de l’objet COM sont routées vers l’assembly d’interopérabilité et transmises à votre application .NET Framework.  
  
 Vous pouvez référencer un objet COM sans utiliser d’assembly d’interopérabilité en incorporant les informations de type de l’objet COM dans un assembly .NET. Pour incorporer des informations de type, affectez à la propriété la valeur `Embed Interop Types` `True` pour la référence à l’objet com. Si vous compilez à l’aide du compilateur de ligne de commande, utilisez l' `/link` option pour référencer la bibliothèque com. Pour plus d’informations, consultez [-Link (Visual Basic)](../../reference/command-line-compiler/link.md).  
  
 Visual Basic crée automatiquement des assemblys d’interopérabilité lorsque vous ajoutez une référence à une bibliothèque de types à partir de l’environnement de développement intégré (IDE). Lorsque vous travaillez à partir de la ligne de commande, vous pouvez utiliser l’utilitaire Tlbimp pour créer manuellement des assemblys d’interopérabilité.  
  
### <a name="to-add-references-to-com-objects"></a>Pour ajouter des références à des objets COM  
  
1. Dans le menu **projet** , choisissez **Ajouter une référence** , puis cliquez sur l’onglet **com** dans la boîte de dialogue.  
  
2. Sélectionnez le composant que vous souhaitez utiliser dans la liste des objets COM.  
  
3. Pour simplifier l’accès à l’assembly d’interopérabilité, ajoutez une `Imports` instruction au début de la classe ou du module dans lequel vous allez utiliser l’objet com. Par exemple, l’exemple de code suivant importe l’espace `INKEDLib` de noms pour les objets référencés dans la `Microsoft InkEdit Control 1.0` bibliothèque.  
  
     [!code-vb[VbVbalrInterop#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#40)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a>Pour créer un assembly d’interopérabilité à l’aide de Tlbimp  
  
1. Ajoutez l’emplacement de Tlbimp au chemin de recherche, s’il ne fait pas déjà partie du chemin de recherche et que vous n’êtes pas actuellement dans le répertoire où il se trouve.  
  
2. Appelez Tlbimp à partir d’une invite de commandes, en fournissant les informations suivantes :  
  
    - Nom et emplacement de la DLL qui contient la bibliothèque de types  
  
    - Nom et emplacement de l’espace de noms où les informations doivent être placées  
  
    - Nom et emplacement de l’assembly d’interopérabilité cible  
  
     Le code suivant est fourni à titre d'exemple :  
  
    ```console  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     Vous pouvez utiliser Tlbimp pour créer des assemblys d’interopérabilité pour les bibliothèques de types, même pour les objets COM non inscrits. Toutefois, les objets COM référencés par les assemblys d’interopérabilité doivent être correctement inscrits sur l’ordinateur sur lequel ils doivent être utilisés. Vous pouvez inscrire un objet COM à l’aide de l’utilitaire regsvr32 inclus dans le système d’exploitation Windows.  
  
## <a name="see-also"></a>Voir aussi

- [COM Interop](index.md)
- [Tlbimp.exe (Type Library Importer)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (exportateur de bibliothèques de types)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [Procédure pas à pas : Implémentation de l’héritage avec les objets COM](walkthrough-implementing-inheritance-with-com-objects.md)
- [Dépannage de l’interopérabilité](troubleshooting-interoperability.md)
- [Imports, instruction (espace de noms et type .NET)](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
