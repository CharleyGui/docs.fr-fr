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
ms.openlocfilehash: 4b948a64a14df7ea79b54b810f734056d57ef406
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964863"
---
# <a name="data-and-data-objects"></a>Données et objets de données
Les données qui sont transférées dans le cadre d’une opération de glisser-déplacer sont stockées dans un objet de données.  Conceptuellement, un objet de données se compose d’une ou plusieurs des paires suivantes:  
  
- <xref:System.Object> Qui contient les données réelles.  
  
- Identificateur de format de données correspondant.  
  
 Les données elles-mêmes peuvent être composées de tout ce qui peut <xref:System.Object>être représenté comme base.  Le format de données correspondant est une chaîne <xref:System.Type> ou fournit une indication sur le format des données.  Les objets de données prennent en charge l’hébergement de plusieurs paires de formats de données/données; Cela permet à un objet de données unique de fournir des données dans plusieurs formats.  
  
<a name="Data_and_Data_Objects"></a>   
## <a name="data-objects"></a>Objets de données  
 Tous les objets de données doivent <xref:System.Windows.IDataObject> implémenter l’interface, qui fournit l’ensemble de méthodes standard suivant qui active et facilite le transfert de données.  
  
|Méthode|Récapitulatif|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|Récupère un objet de données dans un format de données spécifié.|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|Vérifie si les données sont disponibles dans un format spécifié ou peuvent être converties en un format spécifié.|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|Retourne la liste des formats dans lesquels les données de cet objet de données sont stockées ou vers lequel elles peuvent être converties.|  
|<xref:System.Windows.IDataObject.SetData%2A>|Stocke les données spécifiées dans cet objet de données.|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fournit une implémentation de base <xref:System.Windows.IDataObject> de dans <xref:System.Windows.DataObject> la classe. La classe <xref:System.Windows.DataObject> stock est suffisante pour de nombreux scénarios courants de transfert de données.  
  
 Il existe plusieurs formats prédéfinis, tels que bitmap, CSV, fichier, HTML, RTF, chaîne, texte et audio. Pour plus d’informations sur les formats de données prédéfinis fournis <xref:System.Windows.DataFormats> avec [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], consultez la rubrique de référence sur la classe.  
  
 Les objets de données incluent généralement une fonctionnalité permettant de convertir automatiquement les données stockées dans un format dans un format différent lors de l’extraction des données; Cette fonctionnalité est appelée conversion automatique. Lors de l’interrogation des formats de données disponibles dans un objet de données, les formats de données convertibles automatiquement peuvent être filtrés à partir <xref:System.Windows.DataObject.GetFormats%28System.Boolean%29> des <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> formats de données natifs en `false`appelant la méthode ou et en spécifiant le `autoConvert` paramètre comme.  Lors de l’ajout de données à un objet <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29> de données avec la méthode, la conversion automatique des données peut être `autoConvert` interdite en `false`affectant au paramètre la valeur.  
  
<a name="Working_with_Data_Objects"></a>   
## <a name="working-with-data-objects"></a>Utilisation d’objets de données  
 Cette section décrit les techniques courantes de création et d’utilisation des objets de données.  
  
### <a name="creating-new-data-objects"></a>Création d’objets de données  
 La <xref:System.Windows.DataObject> classe fournit plusieurs constructeurs surchargés qui facilitent le remplissage d' <xref:System.Windows.DataObject> une nouvelle instance avec une seule paire de formats de données/données.  
  
 L’exemple de code suivant crée un nouvel objet de données et utilise l’un des constructeurs <xref:System.Windows.DataObject.%23ctor%2A>surchargés (<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>) pour initialiser l’objet de données avec une chaîne et un format de données spécifié.  Dans ce cas, le format de données est spécifié par une chaîne. la <xref:System.Windows.DataFormats> classe fournit un ensemble de chaînes de type prédéfinies. La conversion automatique des données stockées est autorisée par défaut.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 Pour obtenir plus d’exemples de code qui crée un objet de données, consultez [créer un objet de données](how-to-create-a-data-object.md).  
  
### <a name="storing-data-in-multiple-formats"></a>Stockage de données dans plusieurs formats  
 Un objet de données unique peut stocker des données dans plusieurs formats.   L’utilisation stratégique de plusieurs formats de données dans un objet de données unique rend potentiellement l’objet de données utilisable par un large éventail de cibles de dépôt que si un seul format de données peut être représenté.  Notez que, en général, une source de glissement doit être agnostique sur les formats de données qui sont consommables par les cibles de dépôt potentielles.  
  
 L’exemple suivant montre comment utiliser la <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> méthode pour ajouter des données à un objet de données dans plusieurs formats.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a>Interrogation d’un objet de données pour les formats disponibles  
 Étant donné qu’un seul objet de données peut contenir un nombre arbitraire de formats de données, les objets de données incluent des fonctionnalités permettant de récupérer une liste de formats de données disponibles.  
  
 L’exemple de code suivant utilise <xref:System.Windows.DataObject.GetFormats%2A> la surcharge pour obtenir un tableau de chaînes qui dénote tous les formats de données disponibles dans un objet de données (à la fois natif et par conversion automatique).  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 Pour obtenir plus d’exemples de code qui interroge un objet de données pour obtenir des formats de données disponibles, consultez [répertorier les formats de données dans un objet de données](how-to-list-the-data-formats-in-a-data-object.md).  Pour obtenir des exemples d’interrogation d’un objet de données en vue de la présence d’un format de données particulier, consultez [déterminer si un format de données est présent dans un objet de données](how-to-determine-if-a-data-format-is-present-in-a-data-object.md).  
  
### <a name="retrieving-data-from-a-data-object"></a>Récupération de données à partir d’un objet de données  
 La récupération de données à partir d’un objet de données dans un format particulier implique simplement <xref:System.Windows.DataObject.GetData%2A> l’appel de l’une des méthodes et la spécification du format de données souhaité.  L’une des <xref:System.Windows.DataObject.GetDataPresent%2A> méthodes peut être utilisée pour vérifier la présence d’un format de données particulier.  <xref:System.Windows.DataObject.GetData%2A>retourne les données dans un <xref:System.Object>; selon le format de données, cet objet peut être converti en un conteneur spécifique au type.  
  
 L’exemple de code suivant utilise <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> la surcharge pour vérifier si un format de données spécifié est disponible (natif ou par conversion automatique). Si le format spécifié est disponible, l’exemple récupère les données à l’aide de <xref:System.Windows.DataObject.GetData%28System.String%29> la méthode.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 Pour obtenir plus d’exemples de code qui récupère des données à partir d’un objet de données, consultez [récupérer des données dans un format de données particulier](how-to-retrieve-data-in-a-particular-data-format.md).  
  
### <a name="removing-data-from-a-data-object"></a>Suppression de données d’un objet de données  
 Les données ne peuvent pas être supprimées directement d’un objet de données.  Pour supprimer efficacement des données d’un objet de données, procédez comme suit:  
  
1. Créez un objet de données qui contiendra uniquement les données que vous souhaitez conserver.  
  
2. «Copiez» les données souhaitées de l’ancien objet de données vers le nouvel objet de données.  Pour copier les données, utilisez l’une des <xref:System.Windows.DataObject.GetData%2A> méthodes pour récupérer un <xref:System.Object> qui contient les données brutes, <xref:System.Windows.DataObject.SetData%2A> puis utilisez l’une des méthodes pour ajouter les données au nouvel objet de données.  
  
3. Remplacez l’ancien objet de données par le nouveau.  
  
> [!NOTE]
> Les <xref:System.Windows.DataObject.SetData%2A> méthodes ajoutent uniquement des données à un objet de données; elles ne remplacent pas les données, même si les données et le format de données sont exactement identiques à ceux d’un appel précédent. L' <xref:System.Windows.DataObject.SetData%2A> appel de deux fois pour les mêmes données et le même format de données entraînera la présence du format de données/données deux fois dans l’objet de données.
