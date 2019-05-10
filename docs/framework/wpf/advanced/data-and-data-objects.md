---
title: Données et objets de données
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data transfer [WPF], drag-and-drop
- DataFormats class [WPF]
- DataObject class [WPF]
ms.assetid: 5967d557-1867-420f-a524-ae3af78402da
ms.openlocfilehash: 1e573a3fd175d977d437933d5588c1795851ddc6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64627358"
---
# <a name="data-and-data-objects"></a>Données et objets de données
Les données transférées en tant que partie d’une opération de glisser-déplacer sont stockées dans un objet de données.  Conceptuellement, un objet de données se compose d’un ou plusieurs des paires suivantes :  
  
- Un <xref:System.Object> qui contient les données réelles.  
  
- Un identificateur de format de données correspondant.  
  
 Les données proprement dites peuvent se composer de tout ce qui peut être représentée comme une base de <xref:System.Object>.  Le format de données correspondant est une chaîne ou <xref:System.Type> qui fournit une indication sur le format des données est dans.  Objets de données prennent en charge l’hébergement de plusieurs paires de format de données/données ; Cela permet à un objet de données unique fournir des données dans plusieurs formats.  
  
<a name="Data_and_Data_Objects"></a>   
## <a name="data-objects"></a>Objets de données  
 Tous les objets de données doivent implémenter le <xref:System.Windows.IDataObject> interface, qui fournit le jeu standard de méthodes qui activent et faciliter le transfert de données suivant.  
  
|Méthode|Récapitulatif|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|Récupère un objet de données dans un format de données spécifié.|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|Vérifie si les données n’est disponibles dans, ou peuvent être converties en un format spécifié.|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|Retourne une liste de formats dans lesquels les données dans cet objet de données sont stockées dans, ou peuvent être converties en.|  
|<xref:System.Windows.IDataObject.SetData%2A>|Stocke les données spécifiées dans cet objet de données.|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Fournit une implémentation de base de <xref:System.Windows.IDataObject> dans la <xref:System.Windows.DataObject> classe. Le stock <xref:System.Windows.DataObject> classe est suffisante pour de nombreux scénarios de transfert de données courantes.  
  
 Il existe plusieurs formats prédéfinis, tels que bitmap, CSV, fichier, HTML, RTF, chaîne, texte et audio. Pour plus d’informations sur les formats de données prédéfinis fournis avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez le <xref:System.Windows.DataFormats> rubrique de référence de classe.  
  
 Objets de données incluent couramment une fonctionnalité pour convertir automatiquement les données stockées dans un format vers un autre format lors de l’extraction des données ; Cette fonctionnalité est appelée conversion automatique. Lors de l’interrogation pour les formats de données disponibles dans un objet de données, les formats de données convertibles automatiquement peuvent être filtrés à partir des formats de données natifs en appelant le <xref:System.Windows.DataObject.GetFormats%28System.Boolean%29> ou <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> méthode et en spécifiant le `autoConvert` paramètre en tant que `false`.  Lorsque vous ajoutez des données à un objet de données avec le <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29> (méthode), la conversion automatique de données peut être interdite en définissant le `autoConvert` paramètre `false`.  
  
<a name="Working_with_Data_Objects"></a>   
## <a name="working-with-data-objects"></a>Utilisation des objets de données  
 Cette section décrit des techniques courantes pour créer et utiliser des objets de données.  
  
### <a name="creating-new-data-objects"></a>Création de nouveaux objets de données  
 Le <xref:System.Windows.DataObject> classe fournit plusieurs constructeurs surchargés qui facilitent le remplissage d’un nouveau <xref:System.Windows.DataObject> instance avec une paire de format de données/de données unique.  
  
 L’exemple de code suivant crée un nouvel objet de données et utilise l’un des constructeurs surchargés <xref:System.Windows.DataObject.%23ctor%2A>(<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>) pour initialiser l’objet de données avec une chaîne et un format de données spécifié.  Dans ce cas, le format de données est spécifié par une chaîne ; le <xref:System.Windows.DataFormats> classe fournit un ensemble de chaînes de type prédéfini. La conversion automatique des données stockées est autorisée par défaut.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 Pour plus d’exemples de code qui crée un objet de données, consultez [créer un objet de données](how-to-create-a-data-object.md).  
  
### <a name="storing-data-in-multiple-formats"></a>Stockage des données dans plusieurs Formats  
 Un objet de données unique est en mesure de stocker des données dans plusieurs formats.   Utilisation stratégique de plusieurs formats de données dans un objet de données unique rend potentiellement l’objet de données peut consommer un grand nombre de cibles de dépôt que si uniquement un seul format de données peut être représenté.  Notez que, en général, une source de glissement doit être agnostique concernant les formats de données qui sont consommables par les cibles de dépôt potentiels.  
  
 L’exemple suivant montre comment utiliser le <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> méthode pour ajouter des données à un objet de données dans plusieurs formats.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a>Interrogation d’un objet de données pour les Formats disponibles  
 Comme un objet de données unique peut contenir un nombre arbitraire de formats de données, des objets de données incluent des fonctionnalités pour la récupération d’une liste de formats de données disponibles.  
  
 L’exemple de code suivant utilise la <xref:System.Windows.DataObject.GetFormats%2A> surcharge pour obtenir un tableau de chaînes qui désigne tous les formats de données disponibles dans un objet de données (natif et par conversion automatique).  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 Pour plus d’exemples de code qui interroge un objet de données pour les formats de données disponibles, consultez [répertorient les Formats de données dans un objet de données](how-to-list-the-data-formats-in-a-data-object.md).  Pour obtenir des exemples d’interrogation d’un objet de données pour la présence d’un format de données particulier, consultez [déterminer si un Format de données est présent dans un objet de données](how-to-determine-if-a-data-format-is-present-in-a-data-object.md).  
  
### <a name="retrieving-data-from-a-data-object"></a>Récupération des données à partir d’un objet de données  
 Récupération des données à partir d’un objet de données dans un format particulier implique simplement l’appel d’une de la <xref:System.Windows.DataObject.GetData%2A> méthodes et en spécifiant le format de données souhaité.  Parmi les <xref:System.Windows.DataObject.GetDataPresent%2A> méthodes peuvent être utilisées pour vérifier la présence d’un format de données particulier.  <xref:System.Windows.DataObject.GetData%2A> Retourne les données dans un <xref:System.Object>; selon le format de données, cet objet peut être casté en un conteneur spécifique au type.  
  
 L’exemple de code suivant utilise la <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> surcharge pour vérifier si un format de données spécifié est disponible (natif ou par conversion automatique). Si le format spécifié est disponible, l’exemple récupère les données à l’aide de la <xref:System.Windows.DataObject.GetData%28System.String%29> (méthode).  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 Pour plus d’exemples de code qui Récupère des données à partir d’un objet de données, consultez [récupérer les données dans un Format de données particulier](how-to-retrieve-data-in-a-particular-data-format.md).  
  
### <a name="removing-data-from-a-data-object"></a>Suppression des données à partir d’un objet de données  
 Impossible de supprimer directement des données à partir d’un objet de données.  Pour supprimer efficacement des données à partir d’un objet de données, procédez comme suit :  
  
1. Créer un nouvel objet de données qui contiendra uniquement les données que vous souhaitez conserver.  
  
2. « Copier » les données souhaitées à partir de l’ancien objet de données vers le nouvel objet de données.  Pour copier les données, utilisez une de la <xref:System.Windows.DataObject.GetData%2A> méthodes pour récupérer un <xref:System.Object> qui contient les données brutes, puis utilisez une de le <xref:System.Windows.DataObject.SetData%2A> méthodes pour ajouter les données vers le nouvel objet de données.  
  
3. Remplacez l’ancien objet de données par le nouveau.  
  
> [!NOTE]
>  Le <xref:System.Windows.DataObject.SetData%2A> méthodes ajoutent uniquement des données à un objet de données ; ils ne remplacent pas les données, même si les données et le format de données sont exactement les mêmes qu’un appel précédent. Appel de <xref:System.Windows.DataObject.SetData%2A> deux fois pour les données et les données même, format entraîne le format de données/données en double dans l’objet de données.
