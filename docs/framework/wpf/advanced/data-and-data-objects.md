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
ms.openlocfilehash: 532c254f997da183b073ddc9e00b4364ecfcd739
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186337"
---
# <a name="data-and-data-objects"></a>Données et objets de données
Les données transférées dans le cadre d’une opération de drag-and-drop sont stockées dans un objet de données.  Conceptuellement, un objet de données se compose d’une ou de plusieurs des paires suivantes :  
  
- Un <xref:System.Object> qui contient les données réelles.  
  
- Un identifiant de format de données correspondant.  
  
 Les données elles-mêmes peuvent se composer de <xref:System.Object>tout ce qui peut être représenté comme une base .  Le format de données <xref:System.Type> correspondant est une chaîne ou qui fournit un indice sur le format dans lequel se trouve les données.  Les objets de données prennent en charge l’hébergement de plusieurs paires de formats de données/données; cela permet à un seul objet de données de fournir des données en plusieurs formats.  
  
<a name="Data_and_Data_Objects"></a>
## <a name="data-objects"></a>Objets de données  
 Tous les objets <xref:System.Windows.IDataObject> de données doivent implémenter l’interface, qui fournit l’ensemble standard suivant de méthodes qui permettent et facilitent le transfert de données.  
  
|Méthode|Résumé|  
|------------|-------------|  
|<xref:System.Windows.IDataObject.GetData%2A>|Récupère un objet de données dans un format de données spécifié.|  
|<xref:System.Windows.IDataObject.GetDataPresent%2A>|Vérifie si les données sont disponibles dans un format spécifié ou peuvent être converties en un format spécifié.|  
|<xref:System.Windows.IDataObject.GetFormats%2A>|Retourne une liste de formats dans lesquels sont stockées les données de cet objet de données ou vers lesquels elles peuvent être converties.|  
|<xref:System.Windows.IDataObject.SetData%2A>|Stocke les données spécifiées dans cet objet de données.|  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]fournit une mise <xref:System.Windows.IDataObject> en <xref:System.Windows.DataObject> œuvre de base dans la classe. La <xref:System.Windows.DataObject> classe stock est suffisante pour de nombreux scénarios communs de transfert de données.  
  
 Il existe plusieurs formats prédéfinis, tels que bitmap, CSV, fichier, HTML, RTF, chaîne, texte et audio. Pour plus d’informations sur les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]formats <xref:System.Windows.DataFormats> de données prédéfinis fournis, consultez le sujet de référence de la classe.  
  
 Les objets de données comprennent généralement une installation de conversion automatique des données stockées dans un format à un format différent tout en extrayant des données; cette installation est appelée auto-converti. Lors de la requête pour les formats de données disponibles dans un objet de données, <xref:System.Windows.DataObject.GetFormats%28System.Boolean%29> les <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> formats de `autoConvert` données `false`auto-convertibles peuvent être filtrés à partir de formats de données indigènes en appelant le ou la méthode et en spécifiant le paramètre comme .  Lors de l’ajout de <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%2CSystem.Boolean%29> données à un objet de données avec `autoConvert` la `false`méthode, la conversion automatique des données peut être interdite en définissant le paramètre à .  
  
<a name="Working_with_Data_Objects"></a>
## <a name="working-with-data-objects"></a>Travailler avec des objets de données  
 Cette section décrit les techniques courantes de création et de travail avec des objets de données.  
  
### <a name="creating-new-data-objects"></a>Création de nouveaux objets de données  
 La <xref:System.Windows.DataObject> classe fournit plusieurs constructeurs surchargés qui <xref:System.Windows.DataObject> facilitent le peuplement d’une nouvelle instance avec une seule paire de format de données/données.  
  
 L’exemple suivant, le code crée un nouvel objet <xref:System.Windows.DataObject.%23ctor%2A>de<xref:System.Windows.DataObject.%23ctor(System.String,System.Object)>données et utilise l’un des constructeurs surchargés () pour initialiser l’objet de données avec une chaîne et un format de données spécifié.  Dans ce cas, le format de données est spécifié par une chaîne; la <xref:System.Windows.DataFormats> classe fournit un ensemble de chaînes de type prédéfinie. La conversion automatique des données stockées est autorisée par défaut.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
 Pour plus d’exemples de code qui crée un objet de données, voir [Créer un objet de données](how-to-create-a-data-object.md).  
  
### <a name="storing-data-in-multiple-formats"></a>Stockage des données dans plusieurs formats  
 Un seul objet de données est capable de stocker des données en plusieurs formats.   L’utilisation stratégique de plusieurs formats de données dans un seul objet de données rend potentiellement l’objet de données consommable par une plus grande variété de cibles de baisse que si seulement un seul format de données pouvait être représenté.  Notez qu’en général, une source de drag doit être agnostique au sujet des formats de données qui sont consommables par des cibles de baisse potentielles.  
  
 L’exemple suivant montre <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> comment utiliser la méthode pour ajouter des données à un objet de données dans plusieurs formats.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
### <a name="querying-a-data-object-for-available-formats"></a>Interroger un objet de données pour les formats disponibles  
 Étant donné qu’un seul objet de données peut contenir un nombre arbitraire de formats de données, les objets de données comprennent des facilités de récupération d’une liste de formats de données disponibles.  
  
 L’exemple suivant, <xref:System.Windows.DataObject.GetFormats%2A> le code utilise la surcharge pour obtenir un tableau de chaînes indiquant tous les formats de données disponibles dans un objet de données (à la fois natif et par auto-converti).  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
 Pour plus d’exemples de code qui interroge un objet de données pour les formats de données disponibles, voir [Liste des formats de données dans un objet de données](how-to-list-the-data-formats-in-a-data-object.md).  Pour des exemples de requête d’un objet de données pour la présence d’un format de données particulier, voir [Déterminer si un format de données est présent dans un objet de données](how-to-determine-if-a-data-format-is-present-in-a-data-object.md).  
  
### <a name="retrieving-data-from-a-data-object"></a>Récupération des données à partir d’un objet de données  
 La récupération des données d’un objet de données dans <xref:System.Windows.DataObject.GetData%2A> un format particulier implique simplement d’appeler l’une des méthodes et de spécifier le format de données souhaité.  L’une <xref:System.Windows.DataObject.GetDataPresent%2A> des méthodes peut être utilisée pour vérifier la présence d’un format de données particulier.  <xref:System.Windows.DataObject.GetData%2A>retourne les données <xref:System.Object>dans un ; selon le format de données, cet objet peut être jeté à un conteneur spécifique à un type.  
  
 L’exemple suivant, <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> le code utilise la surcharge pour vérifier si un format de données spécifié est disponible (natif ou par auto-converti). Si le format spécifié est disponible, l’exemple <xref:System.Windows.DataObject.GetData%28System.String%29> récupère les données en utilisant la méthode.  
  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
 Pour plus d’exemples de code qui récupère les données d’un objet de données, voir [Retrieve Data in a Particular Data Format](how-to-retrieve-data-in-a-particular-data-format.md).  
  
### <a name="removing-data-from-a-data-object"></a>Suppression des données d’un objet de données  
 Les données ne peuvent pas être directement supprimées d’un objet de données.  Pour supprimer efficacement les données d’un objet de données, suivez ces étapes :  
  
1. Créez un nouvel objet de données qui ne contiendra que les données que vous souhaitez conserver.  
  
2. "Copie" les données souhaitées de l’ancien objet de données à l’objet de nouvelles données.  Pour copier les données, <xref:System.Windows.DataObject.GetData%2A> utilisez l’une des méthodes pour récupérer un <xref:System.Object> <xref:System.Windows.DataObject.SetData%2A> qui contient les données brutes, puis utilisez l’une des méthodes pour ajouter les données au nouvel objet de données.  
  
3. Remplacez l’ancien objet de données par le nouveau.  
  
> [!NOTE]
> Les <xref:System.Windows.DataObject.SetData%2A> méthodes n’ajoutent que des données à un objet de données; ils ne remplacent pas les données, même si le format de données et de données est exactement le même qu’un appel précédent. Le <xref:System.Windows.DataObject.SetData%2A> fait d’appeler deux fois pour le même format de données et de données entraînera la présence du format de données/données deux fois dans l’objet de données.
