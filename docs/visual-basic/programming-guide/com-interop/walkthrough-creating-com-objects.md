---
title: 'Procédure pas à pas : Création d’objets COM'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: 6ff23f73af384a1440bcebd4b6bac21714e01756
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051478"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a>Procédure pas à pas : création d'objets COM avec Visual Basic
Lors de la création d’applications ou de composants, il est préférable de créer des assemblys .NET Framework. Toutefois, Visual Basic permet également d’exposer facilement un composant .NET Framework à COM. Cela vous permet de fournir de nouveaux composants pour les suites d’applications antérieures qui requièrent des composants COM. Cette procédure pas à pas montre comment utiliser Visual Basic pour exposer des objets .NET Framework en tant qu’objets COM, avec et sans le modèle de classe COM.  
  
 Le moyen le plus simple d’exposer des objets COM consiste à utiliser le modèle de classe COM. Ce modèle crée une nouvelle classe, configure votre projet pour générer la classe avec une couche d’interopérabilité comme un objet COM et l’enregistre auprès du système d’exploitation.  
  
> [!NOTE]
> Bien que vous puissiez également exposer une classe créée dans Visual Basic en tant qu’objet COM pour le code non managé à utiliser, il ne s’agit pas d’un objet COM réel et ne peut pas être utilisé par Visual Basic. Pour plus d’informations, consultez [interopérabilité COM dans les Applications .NET Framework](com-interoperability-in-net-framework-applications.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a>Pour créer un objet COM à l’aide du modèle de classe COM  
  
1. Ouvrez un nouveau projet d’application Windows à partir du menu **fichier** en cliquant sur **nouveau projet**.  
  
2. Dans la boîte de dialogue **nouveau projet** , sous le champ **types de projets** , vérifiez que Windows est sélectionné. Sélectionnez **bibliothèque de classes** dans la liste **modèles** , puis cliquez sur **OK**. Le nouveau projet s’affiche.  
  
3. Dans le menu **projet** , sélectionnez **Ajouter un nouvel élément** . La boîte de dialogue **Ajouter un nouvel élément** s’affiche.  
  
4. Sélectionnez **classe com** dans la liste **modèles** , puis cliquez sur **Ajouter**. Visual Basic ajoute une nouvelle classe et configure le nouveau projet pour COM Interop.  
  
5. Ajoutez du code, tel que des propriétés, des méthodes et des événements, à la classe COM.  
  
6. Sélectionnez **générer ClassLibrary1** dans le menu **générer** . Visual Basic génère l’assembly et inscrit l’objet COM auprès du système d’exploitation.  
  
## <a name="creating-com-objects-without-the-com-class-template"></a>Création d’objets COM sans le modèle de classe COM  
 Vous pouvez également créer une classe COM manuellement au lieu d’utiliser le modèle de classe COM. Cette procédure est utile lorsque vous travaillez à partir de la ligne de commande ou lorsque vous souhaitez plus de contrôle sur la façon dont les objets COM sont définis.  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a>Pour configurer votre projet afin de générer un objet COM  
  
1. Ouvrez un nouveau projet d’application Windows à partir du menu **fichier** en cliquant sur **NewProject**.  
  
2. Dans la boîte de dialogue **nouveau projet** , sous le champ **types de projets** , vérifiez que Windows est sélectionné. Sélectionnez **bibliothèque de classes** dans la liste **modèles** , puis cliquez sur **OK**. Le nouveau projet s’affiche.  
  
3. Dans l’**Explorateur de solutions**, cliquez avec le bouton droit sur le projet, puis cliquez sur **Propriétés**. Le **Concepteur de projets** s’affiche.  
  
4. Cliquez sur l’onglet **Compiler**.  
  
5. Activez la case à cocher **inscrire pour COM Interop** .  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a>Pour configurer le code de votre classe afin de créer un objet COM  
  
1. Dans **Explorateur de solutions**, double-cliquez sur **Class1. vb** pour afficher son code.  
  
2. Renommez la classe en `ComClass1`.  
  
3. Ajoutez les constantes suivantes à `ComClass1` . Ils stockent les constantes d’identificateur global unique (GUID) que les objets COM doivent avoir.  
  
     [!code-vb[VbVbalrInterop#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#2)]  
  
4. Dans le menu **Outils**, cliquez sur **Créer un Guid**. Dans la boîte de dialogue **Créer un Guid**, cliquez sur **Format du Registre**, puis sur **Copier**. Cliquez sur **Quitter**.  
  
5. Remplacez la chaîne vide pour `ClassId` par le GUID, en supprimant les accolades de début et de fin. Par exemple, si le GUID fourni par Guidgen est, `"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"` votre code doit se présenter comme suit.  
  
     [!code-vb[VbVbalrInterop#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#3)]  
  
6. Répétez les étapes précédentes pour `InterfaceId` les `EventsId` constantes et, comme dans l’exemple suivant.  
  
     [!code-vb[VbVbalrInterop#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#4)]  
  
    > [!NOTE]
    > Assurez-vous que les GUID sont nouveaux et uniques. dans le cas contraire, votre composant COM risque d’entrer en conflit avec d’autres composants COM.  
  
7. Ajoutez l' `ComClass` attribut à `ComClass1` , en spécifiant les GUID pour l’ID de classe, l’ID d’interface et l’ID d’événements, comme dans l’exemple suivant :  
  
     [!code-vb[VbVbalrInterop#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#5)]  
  
8. Les classes COM doivent avoir un constructeur sans paramètre `Public Sub New()` ou la classe ne sera pas inscrite correctement. Ajoutez un constructeur sans paramètre à la classe :  
  
     [!code-vb[VbVbalrInterop#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#6)]  
  
9. Ajoutez des propriétés, des méthodes et des événements à la classe, en la terminant par une `End Class` instruction. Dans le menu **générer** , sélectionnez **générer la solution** . Visual Basic génère l’assembly et inscrit l’objet COM auprès du système d’exploitation.  
  
    > [!NOTE]
    > Les objets COM que vous générez avec Visual Basic ne peuvent pas être utilisés par d’autres applications Visual Basic, car il ne s’agit pas d’objets COM véritables. Toute tentative d’ajout de références à ces objets COM génère une erreur. Pour plus d’informations, consultez [interopérabilité COM dans les Applications .NET Framework](com-interoperability-in-net-framework-applications.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:Microsoft.VisualBasic.ComClassAttribute>
- [COM Interop](index.md)
- [Procédure pas à pas : Implémentation de l’héritage avec les objets COM](walkthrough-implementing-inheritance-with-com-objects.md)
- [#Region directive](../../language-reference/directives/region-directive.md)
- [Interopérabilité COM dans les applications .NET Framework](com-interoperability-in-net-framework-applications.md)
- [Dépannage de l’interopérabilité](troubleshooting-interoperability.md)
