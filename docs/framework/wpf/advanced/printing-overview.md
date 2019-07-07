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
ms.openlocfilehash: 2090c58369ed3c7bda5df1342291001d9550d48d
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2019
ms.locfileid: "67610470"
---
# <a name="printing-overview"></a>Vue d'ensemble de l'impression
Avec Microsoft .NET Framework, les développeurs d’applications à l’aide de Windows Presentation Foundation (WPF) ont un nouvel ensemble étoffé d’impression et les API de gestion de système d’impression. Avec [!INCLUDE[TLA#tla_winvista](../../../../includes/tlasharptla-winvista-md.md)], certaines de ces améliorations du système d'impression sont aussi accessibles aux développeurs créant des applications [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et à ceux utilisant du code non managé. Le nouveau format de fichier [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] et le chemin d'impression [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] sont au cœur de cette nouvelle fonctionnalité.  
  
 Cette rubrique contient les sections suivantes.  
  
<a name="introduction_to_XPS"></a>   
## <a name="about-xps"></a>À propos de XPS  
 XPS est un format de document électronique, un format de fichier de mise en attente et un langage de description de page. Il s'agit d'un format de document ouvert qui utilise [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)], [!INCLUDE[TLA#tla_opc](../../../../includes/tlasharptla-opc-md.md)] et d'autres normes du secteur pour créer des documents multiplateformes. XPS simplifie le processus par lequel documents numériques sont créées, partagés, imprimés, affichés et archivées. Pour plus d’informations sur XPS, consultez [Documents XPS](/windows/desktop/printdocs/documents).  
  
 Plusieurs techniques pour impression basés sur XPS contenu à l’aide [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sont illustrées dans [imprimer des fichiers XPS par programmation](how-to-programmatically-print-xps-files.md). Il peut vous être utile de vous reporter à ces exemples pendant l'examen du contenu de cette rubrique. (Les développeurs de code non managé doivent consulter documentation pour le [(fonction) MXDC_ESCAPE](/windows/desktop/printdocs/mxdc-escape). Les développeurs Windows Forms doivent utiliser l’API dans le <xref:System.Drawing.Printing> espace de noms qui ne prend pas en charge la version complète [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] chemin d’impression, mais prend en charge un chemin d’impression hybride de GDI vers XPS. Consultez **Architecture du chemin d'impression** ci-dessous.)  
  
<a name="XPS_print_path_intro"></a>   
## <a name="xps-print-path"></a>Chemin d'impression XPS  
 Le chemin d’impression de XML Paper Specification (XPS) est un nouveau [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] fonctionnalité qui redéfinit la gestion de l’impression dans les applications Windows. Étant donné que [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] peut remplacer un langage de présentation de document (tel que RTF), un format de spouleur d’impression (comme WMF) et un langage de description de page (tel que PCL ou Postscript), le nouveau chemin d’impression conserve le format XPS à partir de la publication d’application à la traitement final dans le pilote d’imprimante ou le périphérique.  
  
 Le chemin d’impression de XPS repose sur le modèle de pilote d’imprimante XPS (XPSDrv), qui offre plusieurs avantages pour les développeurs comme [!INCLUDE[TLA#tla_wys](../../../../includes/tlasharptla-wys-md.md)] l’impression, prise en charge de couleur améliorée et considérablement amélioré les performances d’impression. (Pour plus d’informations sur XPSDrv, consultez le [documentation de Windows Driver Kit](/windows-hardware/drivers/).)  
  
 L’opération du spouleur d’impression pour les documents XPS est essentiellement les mêmes que dans les versions précédentes de Windows. Toutefois, il a été amélioré pour prendre en charge le chemin d’impression XPS outre existant [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] chemin d’impression. Le nouveau chemin d’impression consomme en mode natif un fichier de spool XPS. Alors que les pilotes d’imprimante en mode utilisateur écrits pour les versions précédentes de [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] continueront de fonctionner, un pilote d’imprimante XPS (XPSDrv) est requis pour pouvoir utiliser le chemin d’impression XPS.  
  
 Les avantages du chemin d’impression XPS sont significatifs et incluent :  
  
- prise en charge de l'impression [!INCLUDE[TLA2#tla_wys](../../../../includes/tla2sharptla-wys-md.md)] ;  
  
- prise en charge native de profils de couleurs avancés, qui incluent 32 bits par canal (bpc), CMJN, les couleurs nommées, les encres n et prise en charge native de la transparence et des dégradés ;  
  
- Amélioration des performances d’impression pour les deux .NET Framework et [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] en fonction des applications.  
  
- Format XPS standard du secteur.  
  
 Pour les scénarios d’impression de base, une API simple et intuitive est disponible avec un point d’entrée unique pour la soumission de travail, de la configuration et de l’interface utilisateur. Pour les scénarios avancés, une prise en charge supplémentaire est ajoutée pour la personnalisation de l'[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] (ou pas d'[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] du tout), l'impression synchrone ou asynchrone et les fonctions d'impression par lots. Les deux options assurent une prise en charge de l'impression en mode confiance totale ou partielle.  
  
 XPS a été conçu avec l’extensibilité à l’esprit. À l’aide de l’infrastructure d’extensibilité, fonctionnalités et fonctions peuvent être ajoutées au format XPS de manière modulaire. Les fonctionnalités d'extensibilité sont les suivantes :  
  
- Schéma d'impression. Le schéma public est mis à jour régulièrement et permet l’extension rapide des fonctions des appareils. (Consultez **PrintTicket et PrintCapabilities** ci-dessous.)  
  
- Pipeline de filtres extensible. Le pipeline de filtres XPS imprimante pilote (XPSDrv) a été conçu pour permettre l’impression directe et évolutive de documents XPS. Pour plus d’informations, consultez [pilotes d’imprimante XPSDrv](/windows-hardware/drivers/print/xpsdrv-printer-drivers). 
  
### <a name="print-path-architecture"></a>Architecture du chemin d'impression  
 Alors que les deux [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] et les applications .NET Framework prend en charge XPS, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] et les applications Windows Forms utilisent un [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] au format XPS conversion afin de créer XPS au format de contenu pour le pilote d’imprimante XPS (XPSDrv). Ces applications ne sont pas requis pour utiliser le chemin d’impression XPS et pouvez continuer à utiliser [!INCLUDE[TLA#tla_emf](../../../../includes/tlasharptla-emf-md.md)] en fonction de l’impression. Toutefois, la plupart des améliorations et fonctionnalités XPS sont uniquement disponibles pour les applications qui ciblent le chemin d’impression XPS.  
  
 Pour activer l’utilisation d’imprimantes XPSDrv par [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] et applications Windows Forms, le pilote d’imprimante XPS (XPSDrv) prend en charge la conversion de [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] au format XPS mettre en forme. Le modèle XPSDrv fournit également un convertisseur pour XPS à [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] format afin que [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] applications peuvent imprimer [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] Documents. Pour [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications, la conversion de XPS à [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] format est effectué automatiquement par le <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> et <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> méthodes de la <xref:System.Windows.Xps.XpsDocumentWriter> classe chaque fois que la file d’attente d’impression cible de l’opération d’écriture n’a pas de pilote XPSDrv. (Applications Windows Forms ne peuvent pas imprimer [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)] Documents.)  
  
 L’illustration suivante représente le sous-système d’impression et définit les parties fournies par [!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]et celles définies par les fournisseurs de matériel et logiciel :  
  
 ![Capture d’écran montre le que système d’impression XPS.](./media/printing-overview/xml-paper-specification-print-system.png)  
  
### <a name="basic-xps-printing"></a>Impression XPS de base  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] définit une [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] de base et avancée. Pour les applications qui ne nécessitent pas une personnalisation complète impression ou accès à la fonctionnalité XPS complète en charge l’impression définie, la base est disponible. La prise en charge de l'impression de base est exposé via un contrôle de boîte de dialogue d'impression qui nécessite une configuration minime et présente une [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] familière. De nombreuses fonctionnalités XPS sont disponibles à l’aide de ce modèle d’impression simplifié.  
  
#### <a name="printdialog"></a>PrintDialog  
 Le <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> contrôle fournit un point d’entrée unique pour [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], configuration et la soumission de travaux XPS. Pour plus d'informations sur l'instanciation et l'utilisation du contrôle, consultez [Appeler une boîte de dialogue d'impression](how-to-invoke-a-print-dialog.md).  
  
### <a name="advanced-xps-printing"></a>Impression XPS avancée  
 Pour accéder à l’ensemble complet des fonctionnalités XPS, vous devez utiliser l’API d’impression avancée. Plusieurs API pertinentes sont décrites plus en détail ci-dessous. Pour obtenir la liste complète de XPS de chemin d’impression [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], consultez le <xref:System.Windows.Xps> et <xref:System.Printing> références de l’espace de noms.  
  
#### <a name="printticket-and-printcapabilities"></a>PrintTicket et PrintCapabilities  
 Le <xref:System.Printing.PrintTicket> et <xref:System.Printing.PrintCapabilities> classes constituent la base des fonctionnalités avancées de XPS. Ces deux types d'objets sont des structures [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] de fonctionnalités d'impression telles que le classement, l'impression recto verso, l'agrafage, etc. Ces structures sont définies par le schéma d'impression. <xref:System.Printing.PrintTicket> indique à une imprimante comment traiter un travail d'impression. La classe <xref:System.Printing.PrintCapabilities> définit les fonctionnalités d'une imprimante. En interrogeant les fonctionnalités d'une imprimante, un <xref:System.Printing.PrintTicket> peut être créé pour tirer pleinement parti des fonctionnalités prises en charge de l'imprimante. De la même manière, les fonctionnalités non prises en charge peuvent être évitées.  
  
 L'exemple suivant montre comment interroger l'élément <xref:System.Printing.PrintCapabilities> d'une imprimante et créer un <xref:System.Printing.PrintTicket> à l'aide de code.  
  
 [!code-cpp[xpscreate#PrinterCapabilities](~/samples/snippets/cpp/VS_Snippets_Wpf/XpsCreate/CPP/XpsCreate.cpp#printercapabilities)]
 [!code-csharp[xpscreate#PrinterCapabilities](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsCreate/CSharp/XpsCreate.cs#printercapabilities)]
 [!code-vb[xpscreate#PrinterCapabilities](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsCreate/visualbasic/xpscreate.vb#printercapabilities)]  
  
#### <a name="printserver-and-printqueue"></a>PrintServer et PrintQueue  
 La classe <xref:System.Printing.PrintServer> représente un serveur d'impression réseau et la classe <xref:System.Printing.PrintQueue> représente une imprimante et la file d'attente des travaux de sortie qui lui est associée. Ensemble, ces [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] permettent une gestion avancée des travaux d'impression d'un serveur. Un <xref:System.Printing.PrintServer> ou l'une de ses classes dérivées est utilisé pour gérer un <xref:System.Printing.PrintQueue>. La méthode <xref:System.Printing.PrintQueue.AddJob%2A> est utilisée pour insérer un nouveau travail d'impression dans la file d'attente.  
  
 L'exemple suivant montre comment créer un <xref:System.Printing.LocalPrintServer> et comment accéder au <xref:System.Printing.PrintQueue> par défaut associé avec du code.  
  
 [!code-csharp[xpsprint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[xpsprint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
#### <a name="xpsdocumentwriter"></a>XpsDocumentWriter  
 Un <xref:System.Windows.Xps.XpsDocumentWriter>, avec ses nombreuses le <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> et <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> méthodes, est utilisé pour écrire des documents XPS à un <xref:System.Printing.PrintQueue>. Par exemple, le <xref:System.Windows.Xps.XpsDocumentWriter.Write%28System.Windows.Documents.FixedPage%2CSystem.Printing.PrintTicket%29> méthode est utilisée pour générer un document XPS et <xref:System.Printing.PrintTicket> synchrone. Le <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%28System.Windows.Documents.FixedDocument%2CSystem.Printing.PrintTicket%29> méthode est utilisée pour générer un document XPS et <xref:System.Printing.PrintTicket> en mode asynchrone.  
  
 L'exemple suivant montre comment créer un <xref:System.Windows.Xps.XpsDocumentWriter> avec du code.  
  
 [!code-csharp[XpsPrint#PrintQueueSnip](~/samples/snippets/csharp/VS_Snippets_Wpf/XpsPrint/CSharp/XpsPrintHelper.cs#printqueuesnip)]
 [!code-vb[XpsPrint#PrintQueueSnip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XpsPrint/visualbasic/xpsprinthelper.vb#printqueuesnip)]  
  
 Le méthodes <xref:System.Printing.PrintQueue.AddJob%2A> permettent aussi d'imprimer. Consultez [Imprimer des fichiers XPS par programmation](how-to-programmatically-print-xps-files.md). pour plus d'informations.  
  
<a name="GDI_Print_Path_intro"></a>   
## <a name="gdi-print-path"></a>Chemin d'impression GDI  
 Bien que [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications en mode natif prennent en charge que le chemin d’impression XPS, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] et Windows Forms applications peuvent également tirer parti de certaines fonctionnalités XPS. Le pilote d’imprimante XPS (XPSDrv) peut convertir [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] en fonction de sortie au format XPS. Pour les scénarios avancés, la conversion personnalisée du contenu est pris en charge à l’aide de la [Microsoft XPS Document Converter (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-). De même, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] applications peuvent également être exportés vers le [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] chemin d’impression en appelant une de le <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> ou <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> méthodes de la <xref:System.Windows.Xps.XpsDocumentWriter> classe et en désignant une imprimante non-XpsDrv comme la cible de file d’attente.  

Pour les applications qui ne nécessitent pas de fonctionnalités XPS ou prise en charge, actuel [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] chemin d’impression reste inchangé.  
  
- Pour les documents de référence supplémentaires sur le [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] imprimer le chemin d’accès et les différentes options de conversion de XPS, consultez [Microsoft XPS Document Converter (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-) et [pilotes d’imprimante XPSDrv](/windows-hardware/drivers/print/xpsdrv-printer-drivers).  
  
<a name="XPS_Driver_Model_intro"></a>   
## <a name="xpsdrv-driver-model"></a>Modèle de pilote XPSDrv  
 Le chemin d’impression de XPS améliore l’efficacité du spouleur à l’aide de XPS en tant que le format de spouleur d’impression natif lors de l’impression à un XPS-imprimante ou un pilote. Le processus de mise en file d'attente simplifié dispense de la nécessité de générer un fichier spool intermédiaire, tel qu'un fichier de données [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] avant que le document soit mis en file d'attente. Via la plus petite taille de fichier de mise en attente, le chemin d’impression de XPS peut réduire le trafic réseau et améliorer les performances d’impression.  
  
 [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] est un format fermé qui représente la sortie de l'application sous la forme d'une série d'appels dans [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] pour le rendu des services. Contrairement à [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)], le format de spouleur XPS représente le document réel sans nécessiter davantage interprétation lors de sortie vers un pilote d’imprimante basés sur XPS (XPSDrv). Les pilotes peuvent fonctionner directement sur les données dans le format concerné. Ainsi, il n'est plus utile de procéder aux conversions de données et d'espaces de couleurs qu'impose l'utilisation des fichiers [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] et des pilotes d'imprimante [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)].  
  
 Tailles de fichier en attente sont généralement réduites lorsque vous utilisez des Documents XPS qui ciblent un pilote d’imprimante XPS (XPSDrv) par rapport à leurs [!INCLUDE[TLA2#tla_emf](../../../../includes/tla2sharptla-emf-md.md)] équivalents ; Toutefois, il existe des exceptions :  
  
- Un graphique vectoriel très complexe, superposé en plusieurs couches ou mal écrit peut être plus grand qu'une version bitmap du même graphique.  
  
- À des fins d'affichage sur écran, les fichiers XPS incorporent des polices de périphérique, ainsi que des polices basées sur ordinateur, alors que les fichiers spool GDI n'incorporent pas de polices de périphérique. Mais les deux types de polices sont des sous-ensembles (voir ci-dessous) et les pilotes d'imprimante peuvent supprimer les polices de périphérique avant de transmettre le fichier à l'imprimante.  
  
 La réduction de la taille des fichiers spool est exécutée via plusieurs mécanismes :  
  
- **Création de sous-ensembles de polices** : Seuls les caractères utilisés dans le document réel sont stockés dans le fichier XPS.  
  
- **Prise en charge avancée des graphiques** : la prise en charge native des primitives de transparence et de dégradé évite la rastérisation du contenu dans le document [!INCLUDE[TLA2#tla_xps](../../../../includes/tla2sharptla-xps-md.md)].  
  
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
- [Rubriques de guide pratique](printing-how-to-topics.md)
- [Documents dans WPF](documents-in-wpf.md)
- [Documents XPS](/windows/desktop/printdocs/documents)
- [Sérialisation et stockage de documents](document-serialization-and-storage.md)
- [Microsoft XPS Document Converter (MXDC)](/windows/desktop/printdocs/microsoft-xps-document-converter--mxdc-)
