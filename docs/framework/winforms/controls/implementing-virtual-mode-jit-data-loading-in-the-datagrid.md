---
title: Implémentation du mode virtuel avec le chargement de données juste-à-temps dans le contrôle DataGridView Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], just-in-time data loading
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- just-in-time data loading
- DataGridView control [Windows Forms], large data sets
- virtual mode [Windows Forms], just-in-time data loading
ms.assetid: c2a052b9-423c-4ff7-91dc-d8c7c79345f6
ms.openlocfilehash: fa40f1657a433f5f4ade3de25648ca04c37dfa67
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962601"
---
# <a name="implementing-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a>Implémentation du mode virtuel avec le chargement de données juste-à-temps dans le contrôle DataGridView Windows Forms
L’une des raisons d’implémenter le <xref:System.Windows.Forms.DataGridView> mode virtuel dans le contrôle est de récupérer des données uniquement lorsque cela est nécessaire. C’est ce que l’on appelle le *chargement de données juste-à-temps*.  
  
 Si vous utilisez une table très volumineuse dans une base de données distante, par exemple, vous souhaiterez peut-être éviter les retards de démarrage en extrayant uniquement les données nécessaires à l’affichage et à la récupération des données supplémentaires uniquement lorsque l’utilisateur fait défiler les nouvelles lignes dans la vue. Si les ordinateurs clients qui exécutent votre application ont une quantité limitée de mémoire disponible pour le stockage des données, vous pouvez également vouloir ignorer les données inutilisées lors de la récupération de nouvelles valeurs de la base de données.  
  
 Les sections suivantes décrivent comment utiliser un <xref:System.Windows.Forms.DataGridView> contrôle avec un cache juste-à-temps.  
  
 Pour copier le code dans cette rubrique sous la forme d’une liste unique, consultez [Guide pratique pour Implémentez le mode virtuel avec le chargement de données juste-à-temps dans](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)le contrôle DataGridView Windows Forms.  
  
## <a name="the-form"></a>Le formulaire  
 L’exemple de code suivant définit un formulaire contenant un contrôle en <xref:System.Windows.Forms.DataGridView> lecture seule qui interagit avec `Cache` un objet via <xref:System.Windows.Forms.DataGridView.CellValueNeeded> un gestionnaire d’événements. L' `Cache` objet gère les valeurs stockées localement et utilise un `DataRetriever` objet pour récupérer les valeurs de la table Orders de l’exemple de base de données Northwind. L' `DataRetriever` objet, qui implémente l' `IDataPageRetriever` interface requise par la `Cache` classe, est également utilisé pour initialiser les <xref:System.Windows.Forms.DataGridView> lignes et les colonnes du contrôle.  
  
 Les `IDataPageRetriever`types `DataRetriever`, et`Cache` sont décrits plus loin dans cette rubrique.  
  
> [!NOTE]
> Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application. L'utilisation de l'authentification Windows (également appelée sécurité intégrée) offre un moyen plus sûr de contrôler l'accès à une base de données. Pour plus d’informations, consultez [Protection des informations de connexion](../../data/adonet/protecting-connection-information.md).  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#100)]  
  
## <a name="the-idatapageretriever-interface"></a>Interface IDataPageRetriever  
 L’exemple de code suivant définit `IDataPageRetriever` l’interface, qui est implémentée `DataRetriever` par la classe. La seule méthode déclarée dans cette interface est `SupplyPageOfData` la méthode, qui requiert un index de ligne initial et le nombre de lignes dans une même page de données. Ces valeurs sont utilisées par l’implémenteur pour récupérer un sous-ensemble de données à partir d’une source de données.  
  
 Un `Cache` objet utilise une implémentation de cette interface pendant la construction pour charger deux pages initiales de données. Chaque fois qu’une valeur non mise en cache est nécessaire, le cache ignore une de ces pages et demande une nouvelle page contenant la valeur `IDataPageRetriever`de.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#201)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#201](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#201)]  
  
## <a name="the-dataretriever-class"></a>La classe DataRetriever  
 L’exemple de code suivant définit `DataRetriever` la classe, qui implémente `IDataPageRetriever` l’interface pour récupérer des pages de données à partir d’un serveur. La `DataRetriever` classe fournit `Columns` également les `RowCount` propriétés et, que <xref:System.Windows.Forms.DataGridView> le contrôle utilise pour créer les colonnes nécessaires et ajouter le nombre approprié de lignes vides à la <xref:System.Windows.Forms.DataGridView.Rows%2A> collection. L’ajout de lignes vides est nécessaire pour que le contrôle se comporte comme s’il contienne toutes les données de la table. Cela signifie que la case de défilement dans la barre de défilement aura la taille appropriée et que l’utilisateur pourra accéder à n’importe quelle ligne de la table. Les lignes sont remplies par le <xref:System.Windows.Forms.DataGridView.CellValueNeeded> gestionnaire d’événements uniquement lorsqu’elles sont défilées dans la vue.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#200)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#200](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#200)]  
  
## <a name="the-cache-class"></a>Classe de cache  
 L’exemple de code suivant définit `Cache` la classe, qui gère deux pages de données remplies par `IDataPageRetriever` le biais d’une implémentation. La `Cache` classe définit une structure `DataPage` interne, qui contient un <xref:System.Data.DataTable> pour stocker les valeurs dans une page de cache unique et qui calcule les index de ligne qui représentent les limites supérieure et inférieure de la page.  
  
 La `Cache` classe charge deux pages de données au moment de la construction. Chaque fois <xref:System.Windows.Forms.DataGridView.CellValueNeeded> que l’événement demande une valeur `Cache` , l’objet détermine si la valeur est disponible dans l’une de ses deux pages et, le cas échéant, la retourne. Si la valeur n’est pas disponible localement, `Cache` l’objet détermine laquelle de ses deux pages est la plus éloignée des lignes actuellement affichées et remplace la page par une nouvelle contenant la valeur demandée, qu’elle retourne ensuite.  
  
 En supposant que le nombre de lignes dans une page de données est identique au nombre de lignes qui peuvent être affichées à l’écran en même temps, ce modèle permet aux utilisateurs de paginer le tableau pour revenir efficacement à la dernière page affichée.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#300)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#300](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#300)]  
  
## <a name="additional-considerations"></a>Considérations supplémentaires  
 Les exemples de code précédents sont fournis comme une démonstration du chargement juste-à-temps des données. Vous devrez modifier le code pour vos propres besoins pour obtenir une efficacité maximale. Au minimum, vous devrez choisir une valeur appropriée pour le nombre de lignes par page de données dans le cache. Cette valeur est passée au `Cache` constructeur. Le nombre de lignes par page ne doit pas être inférieur au nombre de lignes qui peuvent être affichées simultanément dans votre <xref:System.Windows.Forms.DataGridView> contrôle.  
  
 Pour de meilleurs résultats, vous devez effectuer des tests de performances et d’utilisation afin de déterminer les besoins de votre système et de vos utilisateurs. Vous devez prendre en compte plusieurs facteurs, notamment la quantité de mémoire sur les ordinateurs clients qui exécutent votre application, la bande passante disponible de la connexion réseau utilisée et la latence du serveur utilisé. La bande passante et la latence doivent être déterminées aux heures d’utilisation maximale.  
  
 Pour améliorer les performances de défilement de votre application, vous pouvez augmenter la quantité de données stockées localement. Toutefois, pour améliorer le temps de démarrage, vous devez éviter le chargement initial de trop de données. Vous souhaiterez peut-être `Cache` modifier la classe pour augmenter le nombre de pages de données qu’elle peut stocker. L’utilisation de plusieurs pages de données peut améliorer l’efficacité du défilement, mais vous devrez déterminer le nombre idéal de lignes dans une page de données, en fonction de la bande passante disponible et de la latence du serveur. Avec des pages plus petites, le serveur est accessible plus fréquemment, mais il faut moins de temps pour renvoyer les données demandées. Si la latence est plus importante que la bande passante, vous souhaiterez peut-être utiliser des pages de données plus volumineuses.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Réglage des performances dans le contrôle DataGridView Windows Forms](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Mode virtuel dans le contrôle DataGridView Windows Forms](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [Procédure pas à pas : Implémentation du mode virtuel dans le contrôle DataGridView Windows Forms](implementing-virtual-mode-wf-datagridview-control.md)
- [Guide pratique : Implémenter le mode virtuel avec le chargement de données juste-à-temps dans le contrôle DataGridView Windows Forms](virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)
