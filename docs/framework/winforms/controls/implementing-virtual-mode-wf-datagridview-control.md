---
title: 'Procédure pas à pas : implémenter le mode virtuel dans le contrôle DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- virtual mode [Windows Forms], walkthroughs
- DataGridView control [Windows Forms], large data sets
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 74eb5276-5ab8-4ce0-8005-dae751d85f7c
ms.openlocfilehash: 5db97b321238bc371c94e627a387bd83ca31b58a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746515"
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a>Procédure pas à pas : implémentation du mode virtuel dans le contrôle DataGridView Windows Forms
Lorsque vous souhaitez afficher de très grandes quantités de données tabulaires dans un contrôle <xref:System.Windows.Forms.DataGridView>, vous pouvez affecter à la propriété <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> la valeur `true` et gérer explicitement l’interaction du contrôle avec son magasin de données. Cela vous permet d’affiner les performances du contrôle dans cette situation.  
  
 Le contrôle <xref:System.Windows.Forms.DataGridView> fournit plusieurs événements que vous pouvez gérer pour interagir avec un magasin de données personnalisé. Cette procédure pas à pas vous guide tout au long du processus d’implémentation de ces gestionnaires d’événements. L’exemple de code de cette rubrique utilise une source de données très simple à des fins d’illustration. Dans un paramètre de production, vous chargez généralement uniquement les lignes que vous devez afficher dans un cache, et vous gérez les événements de <xref:System.Windows.Forms.DataGridView> pour interagir avec le cache et le mettre à jour. Pour plus d’informations, consultez [implémentation du mode virtuel avec le chargement de données juste-à-temps dans le contrôle DataGridView Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
  
 Pour copier le code dans cette rubrique sous la forme d’une liste unique, consultez [Comment : implémenter le mode virtuel dans le contrôle DataGridView Windows Forms](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## <a name="creating-the-form"></a>Création du formulaire  
  
#### <a name="to-implement-virtual-mode"></a>Pour implémenter le mode virtuel  
  
1. Créez une classe qui dérive de <xref:System.Windows.Forms.Form> et contient un contrôle <xref:System.Windows.Forms.DataGridView>.  
  
     Le code suivant contient une initialisation de base. Elle déclare certaines variables qui seront utilisées dans les étapes ultérieures, fournit une méthode `Main` et fournit une disposition de formulaire simple dans le constructeur de classe.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2. Implémentez un gestionnaire pour l’événement <xref:System.Windows.Forms.Form.Load> de votre formulaire qui initialise le contrôle <xref:System.Windows.Forms.DataGridView> et remplit le magasin de données avec des exemples de valeurs.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3. Implémentez un gestionnaire pour l’événement <xref:System.Windows.Forms.DataGridView.CellValueNeeded> qui récupère la valeur de cellule demandée à partir du magasin de données ou de l’objet `Customer` actuellement en cours de modification.  
  
     Cet événement se produit chaque fois que le contrôle de <xref:System.Windows.Forms.DataGridView> doit peindre une cellule.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4. Implémentez un gestionnaire pour l’événement <xref:System.Windows.Forms.DataGridView.CellValuePushed> qui stocke une valeur de cellule modifiée dans l’objet `Customer` représentant la ligne modifiée. Cet événement se produit chaque fois que l’utilisateur valide une modification de valeur de cellule.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5. Implémentez un gestionnaire pour l’événement <xref:System.Windows.Forms.DataGridView.NewRowNeeded> qui crée un nouvel objet `Customer` représentant une ligne nouvellement créée.  
  
     Cet événement se produit chaque fois que l’utilisateur entre la ligne pour les nouveaux enregistrements.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6. Implémentez un gestionnaire pour l’événement <xref:System.Windows.Forms.DataGridView.RowValidated> qui enregistre les lignes nouvelles ou modifiées dans le magasin de données.  
  
     Cet événement se produit chaque fois que l’utilisateur modifie la ligne actuelle.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7. Implémentez un gestionnaire pour l’événement <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> qui indique si l’événement <xref:System.Windows.Forms.DataGridView.CancelRowEdit> se produit lorsque l’utilisateur signale la Reversion de ligne en appuyant deux fois sur ÉCHAP en mode édition ou une fois en dehors du mode d’édition.  
  
     Par défaut, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> se produit lors de la réversion de lignes lorsque des cellules de la ligne actuelle ont été modifiées, sauf si la propriété <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> a la valeur `true` dans le gestionnaire d’événements <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>. Cet événement est utile lorsque la portée de validation est déterminée au moment de l’exécution.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8. Implémentez un gestionnaire pour l’événement <xref:System.Windows.Forms.DataGridView.CancelRowEdit> qui ignore les valeurs de l’objet `Customer` représentant la ligne actuelle.  
  
     Cet événement se produit lorsque l’utilisateur signale la Reversion de ligne en appuyant deux fois sur ÉCHAP en mode édition ou une fois en dehors du mode d’édition. Cet événement ne se produit pas si aucune cellule de la ligne actuelle n’a été modifiée ou si la valeur de la propriété <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> a été définie sur `false` dans un gestionnaire d’événements <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. Implémentez un gestionnaire pour l’événement <xref:System.Windows.Forms.DataGridView.UserDeletingRow> qui supprime un objet `Customer` existant du magasin de données ou ignore un objet `Customer` non enregistré représentant une ligne nouvellement créée.  
  
     Cet événement se produit chaque fois que l’utilisateur supprime une ligne en cliquant sur un en-tête de ligne et en appuyant sur la touche Suppr.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. Implémentez une classe `Customers` simple pour représenter les éléments de données utilisés par cet exemple de code.  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a>Test de l'application  
 Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu.  
  
#### <a name="to-test-the-form"></a>Pour tester le formulaire  
  
- Compilez et exécutez l'application.  
  
     Vous verrez un contrôle de <xref:System.Windows.Forms.DataGridView> rempli avec trois enregistrements de client. Vous pouvez modifier les valeurs de plusieurs cellules d’une ligne et appuyer deux fois sur ÉCHAP en mode édition et en dehors du mode d’édition pour rétablir la totalité de la ligne à ses valeurs d’origine. Lorsque vous modifiez, ajoutez ou supprimez des lignes dans le contrôle, `Customer` objets dans le magasin de données sont également modifiés, ajoutés ou supprimés.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cette application vous offre une compréhension de base des événements que vous devez gérer pour implémenter le mode virtuel dans le contrôle <xref:System.Windows.Forms.DataGridView>. Vous pouvez améliorer cette application de base de plusieurs façons :  
  
- Implémentez un magasin de données qui met en cache des valeurs à partir d’une base de données externe. Le cache doit récupérer et ignorer les valeurs selon les besoins afin qu’il ne contienne que ce qui est nécessaire pour l’affichage tout en consommant une petite quantité de mémoire sur l’ordinateur client.  
  
- Ajustez les performances du magasin de données en fonction de vos besoins. Par exemple, vous souhaiterez peut-être compenser les connexions réseau lentes plutôt que les limitations de mémoire de l’ordinateur client en utilisant une taille de cache supérieure et en minimisant le nombre de requêtes de base de données.  
  
 Pour plus d’informations sur la mise en cache des valeurs à partir d’une base de données externe, consultez [Comment : implémenter le mode virtuel avec le chargement de données juste-à-temps dans le contrôle DataGridView Windows Forms](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- <xref:System.Windows.Forms.DataGridView.CellValuePushed>
- <xref:System.Windows.Forms.DataGridView.NewRowNeeded>
- <xref:System.Windows.Forms.DataGridView.RowValidated>
- <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>
- <xref:System.Windows.Forms.DataGridView.CancelRowEdit>
- <xref:System.Windows.Forms.DataGridView.UserDeletingRow>
- [Réglage des performances dans le contrôle DataGridView Windows Forms](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Implémentation du mode virtuel avec le chargement immédiat des données dans le contrôle DataGridView Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [Guide pratique pour implémenter le mode virtuel dans le contrôle DataGridView Windows Forms](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
