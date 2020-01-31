---
title: Vue d'ensemble de l'impression
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print path [WPF], XPS
- printers [WPF], XPSDrv-based
- printing [WPF]
- PrintQueue class PrintServer class [WPF]
- XML Paper Specification (XPS) file format
- XPS (XML Paper Specification) file format
- XPSDrv-based printers
- GDI print path [WPF]
ms.assetid: 0de8ac41-9aa6-413d-a121-7aa6f41539b1
ms.openlocfilehash: de9f4b5c0a817d010c7510395b4e5c09ed0a9865
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794282"
---
# <a name="printing-overview"></a>Vue d'ensemble de l'impression
Avec Microsoft .NET Framework, les développeurs d’applications qui utilisent Windows Presentation Foundation (WPF) disposent d’un nouvel ensemble riche d’API de gestion de système d’impression et d’impression. Avec Windows Vista, certaines de ces améliorations du système d’impression sont également disponibles pour les développeurs qui créent des applications de Windows Forms et des développeurs utilisant du code non managé. Le nouveau format de fichier XPS (XML Paper Specification) et le chemin d’impression XPS sont au cœur de cette nouvelle fonctionnalité.  
  
 Cette rubrique contient les sections suivantes.  
  
<a name="introduction_to_XPS"></a>   
## <a name="about-xps"></a>À propos de XPS  
 XPS est un format de document électronique, un format de fichier de mise en file d’attente et un langage de description de page. Il s’agit d’un format de document ouvert qui utilise XML, Open Packaging Conventions (OPC) et d’autres normes du secteur pour créer des documents multiplateformes. XPS simplifie le processus par lequel les documents numériques sont créés, partagés, imprimés, affichés et archivés. Pour plus d’informations sur XPS, consultez [documents XPS](/windows/desktop/printdocs/documents).  
  
 Plusieurs techniques pour l’impression de contenu XPS à l’aide de WPF sont illustrées dans l' [impression par programme des fichiers XPS](how-to-programmatically-print-xps-files.md). Il peut vous être utile de vous reporter à ces exemples pendant l'examen du contenu de cette rubrique. (Les développeurs de code non managé doivent consulter la documentation de la [fonction MXDC_ESCAPE](/windows/desktop/printdocs/mxdc-escape). Windows Forms les développeurs doivent utiliser l’API dans l’espace de noms <xref:System.Drawing.Printing> qui ne prend pas en charge le chemin d’impression XPS complet, mais prend en charge un chemin d’impression hybride GDI-à-XPS. Consultez **Architecture du chemin d'impression** ci-dessous.)  
  
<a name="XPS_print_path_intro"></a>   
## <a name="xps-print-path"></a>Chemin d'impression XPS  
 Le chemin d’impression XPS (XML Paper Specification) est une nouvelle fonctionnalité de Windows qui redéfinit la façon dont l’impression est gérée dans les applications Windows. Étant donné que XPS peut remplacer un langage de présentation de document (par exemple, RTF), un format de spouleur d’impression (tel que WMF) et un langage de description de page (tel que PCL ou PostScript); le nouveau chemin d’impression conserve le format XPS de la publication de l’application jusqu’au traitement final du pilote d’impression ou de l’appareil.  
  
 Le chemin d’impression XPS repose sur le modèle de pilote d’imprimante XPS (XPSDrv), qui offre plusieurs avantages aux développeurs, tels que l’impression « ce que vous voyez ? » (WYSIWYG), une prise en charge améliorée des couleurs et une amélioration significative des performances d’impression. (Pour plus d’informations sur XPSDrv, consultez la [documentation du kit de pilotes Windows](/windows-hardware/drivers/).)  
  
 Le fonctionnement du spouleur d’impression pour les documents XPS est fondamentalement le même que dans les versions précédentes de Windows. Toutefois, il a été amélioré pour prendre en charge le chemin d’impression XPS en plus du chemin d’impression GDI existant. Le nouveau chemin d’impression utilise en mode natif un fichier de mise en file d’attente XPS. Alors que les pilotes d’imprimante en mode utilisateur écrits pour les versions précédentes de Windows continuent de fonctionner, un pilote d’imprimante XPS (XPSDrv) est nécessaire pour pouvoir utiliser le chemin d’impression XPS.  
  
 Les avantages du chemin d’impression XPS sont significatifs et incluent :  
  
- Prise en charge de l’impression WYSIWYG  
  
- prise en charge native de profils de couleurs avancés, qui incluent 32 bits par canal (bpc), CMJN, les couleurs nommées, les encres n et prise en charge native de la transparence et des dégradés ;  
  
- Performances d’impression améliorées pour les applications .NET Framework et Win32.  
  
- Format XPS standard.  
  
 Pour les scénarios d’impression de base, une API simple et intuitive est disponible avec un seul point d’entrée pour l’interface utilisateur, la configuration et la soumission des travaux. Pour les scénarios avancés, une prise en charge supplémentaire est ajoutée pour la personnalisation de l'[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] (ou pas d'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] du tout), l'impression synchrone ou asynchrone et les fonctions d'impression par lots. Les deux options assurent une prise en charge de l'impression en mode confiance totale ou partielle.  
  
 XPS a été conçu avec l’extensibilité à l’esprit. À l’aide de l’infrastructure d’extensibilité, les fonctionnalités et fonctionnalités peuvent être ajoutées à XPS de manière modulaire. Les fonctionnalités d'extensibilité sont les suivantes :  
  
- Schéma d'impression. Le schéma public est mis à jour régulièrement et permet l’extension rapide des fonctions des appareils. (Consultez **PrintTicket et PrintCapabilities** ci-dessous.)  
  
- Pipeline de filtres extensible. Le pipeline de filtres du pilote d’imprimante XPS (XPSDrv) a été conçu pour permettre l’impression directe et évolutive de documents XPS. Pour plus d’informations, consultez [pilotes d’imprimante XPSDrv](/windows-hardware/drivers/print/xpsdrv-printer-drivers). 
  
### <a name="print-path-architecture"></a>Architecture du chemin d'impression  
 Bien que les applications Win32 et .NET Framework prennent en charge les applications XPS, Win32 et Windows Forms utilisent une conversion GDI-XPS pour créer du contenu au format XPS pour le pilote d’imprimante XPS (XPSDrv). Ces applications ne sont pas tenues d’utiliser le chemin d’impression XPS et peuvent continuer à utiliser l’impression métafichier amélioré (EMF). Toutefois, la plupart des fonctionnalités et améliorations XPS sont uniquement disponibles pour les applications qui ciblent le chemin d’impression XPS.  
  
 Pour permettre l’utilisation d’imprimantes XPSDrv par des applications Win32 et Windows Forms, le pilote d’imprimante XPS (XPSDrv) prend en charge la conversion du format GDI au format XPS. Le modèle XPSDrv fournit également un convertisseur pour les formats XPS à GDI afin que les applications Win32 puissent imprimer des documents XPS. Pour les applications WPF, la conversion du format XPS au format GDI est effectuée automatiquement par les méthodes <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> et <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> de la classe <xref:System.Windows.Xps.XpsDocumentWriter> chaque fois que la file d’attente à l’impression cible de l’opération d’écriture n’a pas de pilote XPSDrv. (Les applications Windows Forms ne peuvent pas imprimer des documents XPS.)  
  
 L’illustration suivante représente le sous-système d’impression et définit les parties fournies par Microsoft, ainsi que les parties définies par les fournisseurs de logiciels et de matériel :  
  
 ![La capture d’écran montre le système d’impression XPS.](./media/printing-overview/xml-paper-specification-print-system.png)  
  
### <a name="basic-xps-printing"></a>Impression XPS de base  
 WPF définit une API de base et avancée. Pour les applications qui ne nécessitent pas une personnalisation étendue de l’impression ou un accès à l’ensemble complet des fonctionnalités XPS, la prise en charge de l’impression de base est disponible. La prise en charge de l'impression de base est exposé via un contrôle de boîte de dialogue d'impression qui nécessite une configuration minime et présente une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] familière. De nombreuses fonctionnalités XPS sont disponibles à l’aide de ce modèle d’impression simplifié.  
  
#### <a name="printdialog"></a>PrintDialog  
 Le contrôle <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> fournit un point d’entrée unique pour l’envoi de [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], de configuration et d’un travail XPS. Pour plus d'informations sur l'instanciation et l'utilisation du contrôle, consultez [Appeler une boîte de dialogue d'impression](how-to-invoke-a-print-dialog.md).  
  
### <a name="advanced-xps-printing"></a>Impression XPS avancée  
 Pour accéder à l’ensemble complet des fonctionnalités XPS, vous devez utiliser l’API d’impression avancée. Plusieurs API pertinentes sont décrites plus en détail ci-dessous. Pour obtenir la liste complète des API de chemin d’impression XPS, consultez les références d’espaces de noms <xref:System.Windows.Xps> et <xref:System.Printing>.  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket et PrintCapabilities  
 Les classes <xref:System.Printing.PrintTicket> et <xref:System.Printing.PrintCapabilities> constituent la base des fonctionnalités XPS avancées. Les deux types d’objets sont des structures au format XML de fonctionnalités d’impression telles que le classement, l’impression recto-verso, l’agrafage, etc. Ces structures sont définies par le schéma d’impression. <xref:System.Printing.PrintTicket> indique à une imprimante comment traiter un travail d'impression. La classe <xref:System.Printing.PrintCapabilities> définit les fonctionnalités d'une imprimante. En interrogeant les fonctionnalités d'une imprimante, un <xref:System.Printing.PrintTicket> peut être créé pour tirer pleinement parti des fonctionnalités prises en charge de l'imprimante. De la même manière, les fonctionnalités non prises en charge peuvent être évitées.  
  
 L'exemple suivant montre comment interroger l'élément <xref:System.Printing.PrintCapabilities> d'une imprimante et créer un <xref:System.Printing.PrintTicket> à l'aide de code.  
  
 [!code-cpp[xpscreate#PrinterCapabilities](~/samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>PrintServer et PrintQueue  
 La classe <xref:System.Printing.PrintServer> représente un serveur d'impression réseau et la classe <xref:System.Printing.PrintQueue> représente une imprimante et la file d'attente des travaux de sortie qui lui est associée. Ensemble, ces API permettent une gestion avancée des travaux d’impression d’un serveur. Un <xref:System.Printing.PrintServer> ou l'une de ses classes dérivées est utilisé pour gérer un <xref:System.Printing.PrintQueue>. La méthode <xref:System.Printing.PrintQueue.AddJob%2A> est utilisée pour insérer un nouveau travail d'impression dans la file d'attente.  
  
 L'exemple suivant montre comment créer un <xref:System.Printing.LocalPrintServer> et comment accéder au <xref:System.Printing.PrintQueue> par défaut associé avec du code.  
  
 [!code-csharp[xpsprint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 Une <xref:System.Windows.Xps.XpsDocumentWriter>, avec ses nombreuses méthodes de <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> et de <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A>, est utilisée pour écrire des documents XPS dans un <xref:System.Printing.PrintQueue>. Par exemple, la méthode <xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29> est utilisée pour générer un document XPS et <xref:System.Printing.PrintTicket> de façon synchrone. La méthode <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29> est utilisée pour générer un document XPS et <xref:System.Printing.PrintTicket> de manière asynchrone.  
  
 L'exemple suivant montre comment créer un <xref:System.Windows.Xps.XpsDocumentWriter> avec du code.  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 Le méthodes <xref:System.Printing.PrintQueue.AddJob%2A> permettent aussi d'imprimer. Consultez [Imprimer des fichiers XPS par programmation](how-to-programmatically-print-xps-files.md). pour plus d'informations.  
  
<a name="GDI_Print_Path_intro"></a>   
## <a name="gdi-print-path"></a>Chemin d'impression GDI  
 Alors que les applications WPF prennent en charge le chemin d’impression XPS en mode natif, les applications Win32 et Windows Forms peuvent également tirer parti de certaines fonctionnalités XPS. Le pilote d’imprimante XPS (XPSDrv) peut convertir la sortie GDI au format XPS. Pour les scénarios avancés, la conversion personnalisée du contenu est prise en charge à l’aide de [Microsoft XPS Document Converter (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-). De même, les applications WPF peuvent également sortir du chemin d’impression GDI en appelant l’une des méthodes <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> ou <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> de la classe <xref:System.Windows.Xps.XpsDocumentWriter> et en désignant une imprimante non-XpsDrv comme file d’attente à l’impression cible.  

Pour les applications qui ne requièrent pas de fonctionnalité ou de prise en charge XPS, le chemin d’accès d’impression GDI actuel reste inchangé.  
  
- Pour obtenir des documents de référence supplémentaires sur le chemin d’impression GDI et les différentes options de conversion XPS, consultez [Microsoft XPS Document Converter (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-) et les [pilotes d’imprimante XPSDrv](/windows-hardware/drivers/print/xpsdrv-printer-drivers).  
  
<a name="XPS_Driver_Model_intro"></a>   
## <a name="xpsdrv-driver-model"></a>Modèle de pilote XPSDrv  
 Le chemin d’impression XPS améliore l’efficacité du spouleur en utilisant XPS comme format de spouleur d’impression natif lors de l’impression sur une imprimante ou un pilote compatible XPS. Le processus de mise en file d’attente simplifié élimine la nécessité de générer un fichier spool intermédiaire, tel qu’un fichier de données EMF, avant que le document soit mis en file d’attente. Grâce aux plus petites tailles de fichier spoule, le chemin d’impression XPS peut réduire le trafic réseau et améliorer les performances d’impression.  
  
 EMF est un format fermé qui représente la sortie de l’application sous la forme d’une série d’appels à GDI pour le rendu des services. Contrairement à EMF, le format de spoule XPS représente le document réel sans nécessiter d’interprétation supplémentaire lors de la sortie vers un pilote d’imprimante basé sur XPS (XPSDrv). Les pilotes peuvent fonctionner directement sur les données dans le format concerné. Cette fonctionnalité élimine les données et les conversions d’espace colorimétrique nécessaires à l’utilisation des fichiers EMF et des pilotes d’impression GDI.  
  
 Les tailles de fichier de mise en file d’attente sont généralement réduites quand vous utilisez des documents XPS qui ciblent un pilote d’imprimante XPS (XPSDrv) par rapport à leurs équivalents EMF. Toutefois, il existe des exceptions :  
  
- Un graphique vectoriel très complexe, superposé en plusieurs couches ou mal écrit peut être plus grand qu'une version bitmap du même graphique.  
  
- À des fins d'affichage sur écran, les fichiers XPS incorporent des polices de périphérique, ainsi que des polices basées sur ordinateur, alors que les fichiers spool GDI n'incorporent pas de polices de périphérique. Mais les deux types de polices sont des sous-ensembles (voir ci-dessous) et les pilotes d'imprimante peuvent supprimer les polices de périphérique avant de transmettre le fichier à l'imprimante.  
  
 La réduction de la taille des fichiers spool est exécutée via plusieurs mécanismes :  
  
- **Création de sous-ensembles de polices** : Seuls les caractères utilisés dans le document réel sont stockés dans le fichier XPS.  
  
- **Prise en charge avancée des graphiques** : La prise en charge native des primitives de transparence et de dégradé évite la pixellisation du contenu dans le document XPS.  
  
- **Identification des ressources communes** : les ressources utilisées plusieurs fois (comme une image qui représente un logo d'entreprise) sont traitées comme des ressources partagées et sont chargées une seule fois.  
  
- **Compression ZIP** : Tous les documents XPS utilisent la compression ZIP.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.PrintDialog>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.PrintQueue>
- [Rubriques pratiques](printing-how-to-topics.md)
- [Documents dans WPF](documents-in-wpf.md)
- [Documents XPS](/windows/desktop/printdocs/documents)
- [Sérialisation et stockage de documents](document-serialization-and-storage.md)
- [Microsoft XPS Document Converter (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)
