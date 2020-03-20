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
ms.openlocfilehash: 902d51341850b5245b9fa6410b1954b2ab373bbc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187199"
---
# <a name="printing-overview"></a>Vue d'ensemble de l'impression
Avec Microsoft .NET Framework, les développeurs d’applications utilisant Windows Presentation Foundation (WPF) ont un nouvel ensemble riche d’API de gestion des systèmes d’impression et d’impression. Avec Windows Vista, certaines de ces améliorations du système d’impression sont également disponibles pour les développeurs créant des applications et des développeurs Windows Forms à l’aide de code non gémandé. Au cœur de cette nouvelle fonctionnalité se trouve le nouveau format de fichier XML Paper Specification (XPS) et le chemin d’impression XPS.  
  
 Cette rubrique contient les sections suivantes.  
  
<a name="introduction_to_XPS"></a>
## <a name="about-xps"></a>À propos de XPS  
 XPS est un format de document électronique, un format de fichier de bobine et un langage de description de page. Il s’agit d’un format de document ouvert qui utilise XML, Open Packaging Conventions (OPC), et d’autres normes de l’industrie pour créer des documents multiplateformes. XPS simplifie le processus par lequel les documents numériques sont créés, partagés, imprimés, consultés et archivés. Pour plus d’informations sur XPS, voir [XPS Documents](/windows/desktop/printdocs/documents).  
  
 Plusieurs techniques d’impression de contenu basé sur XPS à l’aide de WPF sont démontrées dans [les fichiers XPS d’impression programmatique](how-to-programmatically-print-xps-files.md). Il peut vous être utile de vous reporter à ces exemples pendant l'examen du contenu de cette rubrique. (Les développeurs de code non-gestion devraient voir la documentation pour la [fonction MXDC_ESCAPE](/windows/desktop/printdocs/mxdc-escape). Les développeurs de formulaires Windows <xref:System.Drawing.Printing> doivent utiliser l’API dans l’espace de nom qui ne prend pas en charge la voie d’impression XPS complète, mais prend en charge un mode d’impression hybride GDI-to-XPS. Consultez **Architecture du chemin d'impression** ci-dessous.)  
  
<a name="XPS_print_path_intro"></a>
## <a name="xps-print-path"></a>Chemin d'impression XPS  
 Le chemin d’impression XML Paper Specification (XPS) est une nouvelle fonctionnalité Windows qui redéfinit la façon dont l’impression est gérée dans les applications Windows. Étant donné que XPS peut remplacer un langage de présentation de documents (comme RTF), un format de bobine d’impression (comme WMF) et un langage de description de page (comme PCL ou Postscript); le nouveau chemin d’impression maintient le format XPS de la publication d’application au traitement final dans le pilote d’impression ou l’appareil.  
  
 Le chemin d’impression XPS est construit sur le modèle de pilote d’imprimante XPS (XPSDrv), qui offre plusieurs avantages pour les développeurs tels que "ce que vous voyez est ce que vous obtenez" (WYSIWYG) impression, un meilleur support couleur, et des performances d’impression considérablement améliorée. (Pour en savoir plus sur XPSDrv, voir la [documentation Windows Driver Kit](/windows-hardware/drivers/).)  
  
 Le fonctionnement du bobine d’impression pour les documents XPS est essentiellement le même que dans les versions précédentes de Windows. Cependant, il a été amélioré pour soutenir le chemin d’impression XPS en plus de la trajectoire d’impression GDI existante. Le nouveau chemin d’impression consomme nativement un fichier de bobine XPS. Alors que les pilotes d’imprimantes en mode utilisateur écrits pour les versions précédentes de Windows continueront à fonctionner, un pilote d’imprimante XPS (XPSDrv) est nécessaire afin d’utiliser le chemin d’impression XPS.  
  
 Les avantages du chemin d’impression XPS sont importants, et comprennent:  
  
- Support d’impression WYSIWYG  
  
- prise en charge native de profils de couleurs avancés, qui incluent 32 bits par canal (bpc), CMJN, les couleurs nommées, les encres n et prise en charge native de la transparence et des dégradés ;  
  
- Amélioration des performances d’impression pour les applications basées sur .NET Framework et Win32.  
  
- Format XPS standard de l’industrie.  
  
 Pour les scénarios d’impression de base, une API simple et intuitive est disponible avec un seul point d’entrée pour l’interface utilisateur, la configuration et la soumission d’emploi. Pour les scénarios avancés, une prise en charge supplémentaire est ajoutée pour la personnalisation de l'[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] (ou pas d'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] du tout), l'impression synchrone ou asynchrone et les fonctions d'impression par lots. Les deux options assurent une prise en charge de l'impression en mode confiance totale ou partielle.  
  
 XPS a été conçu avec l’extéabilité à l’esprit. En utilisant le cadre d’extivité, les fonctionnalités et les capacités peuvent être ajoutées à XPS d’une manière modulaire. Les fonctionnalités d'extensibilité sont les suivantes :  
  
- Schéma d'impression. Le schéma public est mis à jour régulièrement et permet l’extension rapide des fonctions des appareils. (Consultez **PrintTicket et PrintCapabilities** ci-dessous.)  
  
- Pipeline de filtres extensible. Le pipeline de filtres XPS (XPSDrv) a été conçu pour permettre l’impression directe et évolutive des documents XPS. Pour plus d’informations, voir [XPSDrv Printer Drivers](/windows-hardware/drivers/print/xpsdrv-printer-drivers).
  
### <a name="print-path-architecture"></a>Architecture du chemin d'impression  
 Alors que les applications Cadre Win32 et .NET prennent en charge XPS, les applications Win32 et Windows Forms utilisent une conversion GDI à XPS afin de créer du contenu formaté XPS pour le pilote d’imprimante XPS (XPSDrv). Ces applications ne sont pas tenues d’utiliser la trajectoire d’impression XPS et peuvent continuer à utiliser l’impression basée sur le Metafile amélioré (EMF). Cependant, la plupart des fonctionnalités et des améliorations XPS ne sont disponibles que pour les applications qui ciblent la trajectoire d’impression XPS.  
  
 Pour permettre l’utilisation d’imprimantes basées sur XPSDrv par les applications Win32 et Windows Forms, le pilote d’imprimante XPS (XPSDrv) prend en charge la conversion de GDI en format XPS. Le modèle XPSDrv fournit également un convertisseur pour XPS au format GDI afin que les applications Win32 puissent imprimer des documents XPS. Pour les applications WPF, la conversion de XPS <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> au format <xref:System.Windows.Xps.XpsDocumentWriter> GDI se fait automatiquement par les méthodes et méthodes de la classe chaque fois que la file d’attente d’impression cible de l’opération d’écriture n’a pas de pilote XPSDrv. (Les applications Windows Forms ne peuvent pas imprimer des documents XPS.)  
  
 L’illustration suivante décrit le sous-système d’impression et définit les parties fournies par Microsoft, et les parties définies par les logiciels et les fournisseurs de matériel :  
  
 ![Capture d’écran montre le système d’impression XPS.](./media/printing-overview/xml-paper-specification-print-system.png)  
  
### <a name="basic-xps-printing"></a>Impression XPS de base  
 WPF définit à la fois une API de base et avancée. Pour les applications qui ne nécessitent pas de personnalisation d’impression étendue ou l’accès à l’ensemble complet de fonctionnalités XPS, le support d’impression de base est disponible. La prise en charge de l'impression de base est exposé via un contrôle de boîte de dialogue d'impression qui nécessite une configuration minime et présente une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] familière. De nombreuses fonctionnalités XPS sont disponibles à l’aide de ce modèle d’impression simplifié.  
  
#### <a name="printdialog"></a>PrintDialog  
 Le <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> contrôle fournit un [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]point d’entrée unique pour, configuration, et la soumission de travail XPS. Pour plus d'informations sur l'instanciation et l'utilisation du contrôle, consultez [Appeler une boîte de dialogue d'impression](how-to-invoke-a-print-dialog.md).  
  
### <a name="advanced-xps-printing"></a>Impression XPS avancée  
 Pour accéder à l’ensemble complet des fonctionnalités XPS, l’API d’impression avancée doit être utilisée. Plusieurs API pertinentes sont décrites plus en détail ci-dessous. Pour une liste complète des API de <xref:System.Windows.Xps> <xref:System.Printing> chemin d’impression XPS, consultez les références et les références de namespace.  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket et PrintCapabilities  
 Les <xref:System.Printing.PrintTicket> <xref:System.Printing.PrintCapabilities> cours et les classes sont la base des fonctionnalités XPS avancées. Les deux types d’objets sont des structures formatées XML de fonctionnalités orientées vers l’impression telles que la collation, l’impression recestre, les stapling, etc. Ces structures sont définies par le schéma d’impression. <xref:System.Printing.PrintTicket> indique à une imprimante comment traiter un travail d'impression. La classe <xref:System.Printing.PrintCapabilities> définit les fonctionnalités d'une imprimante. En interrogeant les fonctionnalités d'une imprimante, un <xref:System.Printing.PrintTicket> peut être créé pour tirer pleinement parti des fonctionnalités prises en charge de l'imprimante. De la même manière, les fonctionnalités non prises en charge peuvent être évitées.  
  
 L'exemple suivant montre comment interroger l'élément <xref:System.Printing.PrintCapabilities> d'une imprimante et créer un <xref:System.Printing.PrintTicket> à l'aide de code.  
  
 [!code-cpp[xpscreate#PrinterCapabilities](~/samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>PrintServer et PrintQueue  
 La classe <xref:System.Printing.PrintServer> représente un serveur d'impression réseau et la classe <xref:System.Printing.PrintQueue> représente une imprimante et la file d'attente des travaux de sortie qui lui est associée. Ensemble, ces API permettent la gestion avancée des travaux d’impression d’un serveur. Un <xref:System.Printing.PrintServer> ou l'une de ses classes dérivées est utilisé pour gérer un <xref:System.Printing.PrintQueue>. La méthode <xref:System.Printing.PrintQueue.AddJob%2A> est utilisée pour insérer un nouveau travail d'impression dans la file d'attente.  
  
 L'exemple suivant montre comment créer un <xref:System.Printing.LocalPrintServer> et comment accéder au <xref:System.Printing.PrintQueue> par défaut associé avec du code.  
  
 [!code-csharp[xpsprint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 Un <xref:System.Windows.Xps.XpsDocumentWriter>, avec <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> ses <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> nombreuses méthodes et méthodes, est <xref:System.Printing.PrintQueue>utilisé pour écrire des documents XPS à un . Par exemple, <xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29> la méthode est utilisée pour <xref:System.Printing.PrintTicket> produire un document XPS et de façon synchrone. La <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29> méthode est utilisée pour produire <xref:System.Printing.PrintTicket> un document XPS et asynchrone.  
  
 L'exemple suivant montre comment créer un <xref:System.Windows.Xps.XpsDocumentWriter> avec du code.  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 Le méthodes <xref:System.Printing.PrintQueue.AddJob%2A> permettent aussi d'imprimer. Consultez [Imprimer des fichiers XPS par programmation](how-to-programmatically-print-xps-files.md). pour plus d’informations.  
  
<a name="GDI_Print_Path_intro"></a>
## <a name="gdi-print-path"></a>Chemin d'impression GDI  
 Alors que les applications WPF prennent en charge le parcours d’impression XPS, les applications Win32 et Windows Forms peuvent également tirer parti de certaines fonctionnalités XPS. Le pilote d’imprimante XPS (XPSDrv) peut convertir la sortie basée sur GDI en format XPS. Pour les scénarios avancés, la conversion personnalisée du contenu est prise en charge à l’aide du [convertisseur de documents Microsoft XPS (MXDC).](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-) De même, les applications WPF peuvent également sortir sur <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> le chemin <xref:System.Windows.Xps.XpsDocumentWriter> d’impression GDI en appelant l’une des méthodes ou méthodes de la classe et en désignant une imprimante non-XpsDrv comme la file d’attente d’impression cible.  

Pour les applications qui ne nécessitent pas de fonctionnalitéS XPS ou de prise en charge, la trajectoire d’impression GDI actuelle reste inchangée.  
  
- Pour d’autres documents de référence sur la trajectoire d’impression GDI et les différentes options de conversion XPS, voir [Microsoft XPS Document Converter (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-) et [XPSDrv Printer Drivers](/windows-hardware/drivers/print/xpsdrv-printer-drivers).  
  
<a name="XPS_Driver_Model_intro"></a>
## <a name="xpsdrv-driver-model"></a>Modèle de pilote XPSDrv  
 Le chemin d’impression XPS améliore l’efficacité du bobine en utilisant XPS comme format de bobine d’impression native lors de l’impression à une imprimante ou un pilote compatible XPS. Le processus simplifié de bobine élimine la nécessité de générer un fichier de bobine intermédiaire, tel qu’un fichier de données EMF, avant que le document ne soit enroulé. Grâce à de plus petites tailles de fichiers de bobine, le chemin d’impression XPS peut réduire le trafic réseau et améliorer les performances d’impression.  
  
 EMF est un format fermé qui représente la sortie des applications comme une série d’appels dans GDI pour les services de rendu. Contrairement à EMF, le format de bobine XPS représente le document réel sans nécessiter d’interprétation supplémentaire lors de la sortie à un pilote d’imprimante XPS (XPSDrv). Les pilotes peuvent fonctionner directement sur les données dans le format concerné. Cette fonctionnalité élimine les conversions de données et d’espaces de couleur requises lorsque vous utilisez des fichiers EMF et des pilotes d’impression basés sur GDI.  
  
 La taille des fichiers de bobine est généralement réduite lorsque vous utilisez des documents XPS qui ciblent un pilote d’imprimante XPS (XPSDrv) par rapport à leurs équivalents EMF; cependant, il y a des exceptions :  
  
- Un graphique vectoriel très complexe, superposé en plusieurs couches ou mal écrit peut être plus grand qu'une version bitmap du même graphique.  
  
- À des fins d'affichage sur écran, les fichiers XPS incorporent des polices de périphérique, ainsi que des polices basées sur ordinateur, alors que les fichiers spool GDI n'incorporent pas de polices de périphérique. Mais les deux types de polices sont des sous-ensembles (voir ci-dessous) et les pilotes d'imprimante peuvent supprimer les polices de périphérique avant de transmettre le fichier à l'imprimante.  
  
 La réduction de la taille des fichiers spool est exécutée via plusieurs mécanismes :  
  
- **Création de sous-ensembles de polices** : Seuls les caractères utilisés dans le document réel sont stockés dans le fichier XPS.  
  
- **Prise en charge avancée des graphiques** : Le soutien des Autochtones à la transparence et aux primitifs de gradient évite la rasterisation du contenu dans le document XPS.  
  
- **Identification des ressources communes** : les ressources utilisées plusieurs fois (comme une image qui représente un logo d'entreprise) sont traitées comme des ressources partagées et sont chargées une seule fois.  
  
- **Compression ZIP**. Tous les documents XPS utilisent la compression ZIP.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.PrintDialog>
- <xref:System.Windows.Xps.XpsDocumentWriter>
- <xref:System.Windows.Xps.Packaging.XpsDocument>
- <xref:System.Printing.PrintTicket>
- <xref:System.Printing.PrintCapabilities>
- <xref:System.Printing.PrintServer>
- <xref:System.Printing.PrintQueue>
- [Sujets comment se passer](printing-how-to-topics.md)
- [Documents dans WPF](documents-in-wpf.md)
- [Documents XPS](/windows/desktop/printdocs/documents)
- [Sérialisation et stockage de documents](document-serialization-and-storage.md)
- [Convertisseur de documents Microsoft XPS (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)
