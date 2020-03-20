---
title: Fonctionnalités des polices OpenType
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [WPF], OpenType
- typography [WPF], OpenType font technology
- OpenType font technology [WPF]
ms.assetid: 4061a9d1-fe8b-4921-9e17-18ec7d2e3ea2
ms.openlocfilehash: 52fe73bccd625c9508b398874fd6b075af2445e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186807"
---
# <a name="opentype-font-features"></a>Fonctionnalités des polices OpenType

Ce sujet fournit un aperçu de quelques-unes des [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]caractéristiques clés de la technologie de police OpenType dans .  
  
<a name="overview"></a>
## <a name="opentype-font-format"></a>Format des polices OpenType  
 Le format de police OpenType est une extension du format de police TrueType®, ajoutant la prise en charge des données de police PostScript. Le format de police OpenType a été développé conjointement par Microsoft et Adobe Corporation. Les polices OpenType et les services du système d’exploitation qui prennent en charge les polices OpenType offrent aux utilisateurs un moyen simple d’installer et d’utiliser des polices, que les polices contiennent des contours TrueType ou les contours de CFF (PostScript).  
  
 Le format de police OpenType répond aux défis suivants des développeurs :  
  
- Prise en charge multi-plateforme élargie.  
  
- Meilleure prise en charge des jeux de caractères internationaux.  
  
- Meilleure protection des données de police.  
  
- Taille des fichiers plus petite permettant une distribution plus efficace des polices.  
  
- Prise en charge élargie des contrôles typographiques avancés.  
  
> [!NOTE]
> Le Windows SDK contient un ensemble de polices OpenType échantillon que vous pouvez utiliser avec [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] des applications. Ces polices offrent la plupart des fonctionnalités illustrées dans le reste de cette rubrique. Pour plus d’informations, voir [Sample OpenType Font Pack](sample-opentype-font-pack.md).  
  
Pour plus de détails sur le format de police OpenType, consultez la [spécification OpenType](https://docs.microsoft.com/typography/opentype/spec/).  
  
### <a name="advanced-typographic-extensions"></a>Extensions typographiques avancées  
 Les tables typographiques avancées (tables OpenType Layout) étendent la fonctionnalité des polices avec des contours TrueType ou CFF. Les polices OpenType Layout contiennent des informations supplémentaires qui étendent les capacités des polices pour soutenir une typographie internationale de haute qualité. La plupart des polices OpenType n’exposent qu’un sous-ensemble des fonctionnalités OpenType totales disponibles. Les polices OpenType fournissent les caractéristiques suivantes.  
  
- Mappage riche entre les caractères et les glyphes qui prennent en charge les ligatures, les formes positionnelles, les alternatives et les substitutions de police.  
  
- Prise en charge du positionnement à deux dimensions et de l’attachement de glyphes.  
  
- Présence d’informations explicites de script et de langage dans la police, ce qui permet à une application de traitement de texte d’ajuster son comportement en conséquence.  
  
 Les tables OpenType Layout sont décrites plus en détail dans la section [« Tables de fichiers de font »](https://www.microsoft.com/typography/otspec/otff.htm) de la spécification OpenType.  
  
 Le reste de cette vue introduit l’étendue et la flexibilité de certaines des caractéristiques visuellement intéressantes OpenType qui sont exposés par les propriétés de l’objet. <xref:System.Windows.Documents.Typography> Pour plus d’informations sur cet objet, consultez [Classe Typography](#typography_class).  
  
<a name="variants"></a>
## <a name="variants"></a>Variantes  
 Les variantes servent à restituer différents styles typographiques, tels que les exposants et les indices.  
  
### <a name="superscripts-and-subscripts"></a>Exposants et indices  
 La <xref:System.Windows.Documents.Typography.Variants%2A> propriété vous permet de définir des valeurs de superscript et de sous-scripte pour une police OpenType.  
  
 Le texte suivant présente des exposants avec la police Palatino Linotype.  
  
 ![Texte utilisant des exposants OpenType](./media/opentype-font-features/opentype-superscripts.gif "Texte utilisant des exposants OpenType")  
  
 L’exemple de balisage suivant montre comment définir les superscripts <xref:System.Windows.Documents.Typography> pour la police Palatino Linotype, en utilisant les propriétés de l’objet.  
  
 [!code-xaml[OpenTypeFontSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#12)]  
  
 Le texte suivant présente des indices avec la police Palatino Linotype.  
  
 ![Texte utilisant des indices OpenType](./media/opentype-font-features/opentype-subscripts.gif "Texte utilisant des indices OpenType")  
  
 L’exemple de balisage suivant montre comment définir des sous-scriptes <xref:System.Windows.Documents.Typography> pour la police Palatino Linotype, en utilisant les propriétés de l’objet.  
  
 [!code-xaml[OpenTypeFontSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#13)]  
  
### <a name="decorative-uses-of-superscripts-and-subscripts"></a>Utilisations décoratives d’exposants et d’indices  
 Vous pouvez aussi utiliser des exposants et des indices pour créer des effets décoratifs de texte à casse mixte. Le texte suivant présente des exposants et des indices avec la police Palatino Linotype. Notez que les majuscules ne sont pas affectées.  
  
 ![Texte utilisant des exposants et des indices OpenType](./media/opentype-font-features/opentype-superscripts-subscripts.gif "Texte utilisant des exposants et des indices OpenType")  

 L’exemple de balisage suivant montre comment définir les superscripteurs <xref:System.Windows.Documents.Typography> et les sous-scripts pour une police, en utilisant les propriétés de l’objet.  
  
 [!code-xaml[OpenTypeFontSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#14)]  
  
<a name="capitals"></a>
## <a name="capitals"></a>Majuscules  
 Les majuscules représentent un jeu de formes typographiques qui restituent le texte dans des glyphes de type majuscule. En règle générale, quand le texte est entièrement restitué en majuscules, l’espacement entre les lettres peut sembler trop serré et le poids et la proportion des lettres trop lourds. OpenType prend en charge un certain nombre de formats de style pour les capitales, y compris les petites capitales, les petites capitales, les titres et l’espacement des capitaux. Ces formats de style permettent de contrôler l’apparence des majuscules.  
  
 Le texte suivant présente des majuscules standard avec la police Pescadero, suivies de lettres de type « SmallCaps » et « AllSmallCaps ». Dans ce cas, la taille de police utilisée est identique pour les trois mots.  
  
 ![Texte utilisant des majuscules OpenType](./media/opentype-font-features/opentype-capitals.gif "Texte utilisant des majuscules OpenType")  
  
 L’exemple de balisage suivant montre comment définir les majuscules pour la police Pescadero, en utilisant les propriétés de l’objet. <xref:System.Windows.Documents.Typography> Quand le format « SmallCaps » est utilisé, les majuscules de début sont ignorées.  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
### <a name="titling-capitals"></a>Majuscules de titres  
 Le poids et les proportions des majuscules de titres ont été réduits pour leur conférer un aspect plus élégant que les majuscules normales. Les majuscules de titres sont généralement utilisées dans les titres avec des tailles de police supérieures. Le texte suivant présente des majuscules normales et des majuscules de titres avec la police Pescadero. Comme vous pouvez le constater, le plein est plus fin dans le texte de la deuxième ligne.  
  
 ![Texte utilisant des majuscules de titres OpenType](./media/opentype-font-features/opentype-titling-capitals.gif "Texte utilisant des majuscules de titres OpenType")  
  
 L’exemple de balisage suivant montre comment définir les majuscules <xref:System.Windows.Documents.Typography> de titrage pour la police Pescadero, en utilisant les propriétés de l’objet.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet17](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet17)]  
  
### <a name="capital-spacing"></a>Espacement des majuscules  
 L’espacement des majuscules est une fonctionnalité qui permet d’accroître l’espacement du texte quand celui-ci se compose uniquement de majuscules. Les majuscules sont généralement conçues pour se mêler aux minuscules. L’espacement employé entre une majuscule et une minuscule peut paraître trop serré quand toutes les lettres sont des majuscules. Le texte suivant présente l’espacement normal et l’espacement de majuscules avec la police Pescadero.  
  
 ![Texte utilisant l'espacement des majuscules OpenType](./media/opentype-font-features/opentype-capital-spacing.gif "Texte utilisant l'espacement des majuscules OpenType")  

 L’exemple de balisage suivant montre comment définir l’espacement du <xref:System.Windows.Documents.Typography> capital pour la police Pescadero, en utilisant les propriétés de l’objet.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet18](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet18)]  
  
<a name="ligatures"></a>
## <a name="ligatures"></a>Ligatures  
 Une ligature est un glyphe formé de deux ou plusieurs glyphes dans le but de créer un texte plus lisible ou esthétique. Les polices OpenType prennent en charge quatre types de ligatures :  
  
- **Ligatures standard** : conçues pour améliorer la lisibilité. Par exemple, « fi », « fl » et « ff » sont des ligatures standard.  
  
- **Ligatures contextuelles** : conçues pour améliorer la lisibilité en offrant un meilleur comportement de jointure entre les caractères qui composent la ligature.  
  
- **Ligatures discrétionnaires** : conçues à des fins esthétiques et pas spécifiquement pour la lisibilité.  
  
- **Ligatures historiques** : conçues en fonction de critères historiques et pas spécifiquement pour la lisibilité.  
  
 Le texte suivant présente des glyphes à ligatures standard avec la police Pericles.  
  
 ![Texte utilisant des ligatures standard OpenType](./media/opentype-font-features/opentype-standard-ligatures.gif "Texte utilisant des ligatures standard OpenType")  
  
 L’exemple de balisage suivant montre comment définir les glyphes standard <xref:System.Windows.Documents.Typography> de ligature pour la police De Périclès, en utilisant les propriétés de l’objet.  
  
 [!code-xaml[OpenTypeFontSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#4)]  
  
 Le texte suivant présente des glyphes à ligatures discrétionnaires avec la police Pericles.  
  
 ![Texte utilisant des ligatures discrétionnaires OpenType](./media/opentype-font-features/opentype-discretionary-ligatures.gif "Texte utilisant des ligatures discrétionnaires OpenType")  
  
 L’exemple de balisage suivant montre comment définir les glyphes de <xref:System.Windows.Documents.Typography> ligature discrétionnaire pour la police Périclès, en utilisant les propriétés de l’objet.  
  
 [!code-xaml[OpenTypeFontSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#5)]  
  
 Par défaut, les polices [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] OpenType dans les ligatures standard. Par exemple, si vous utilisez la police Palatino Linotype, les ligatures standard « fi », « ff » et « fl » apparaissent comme un glyphe de caractères combinés. Notez que les deux caractères de chaque ligature standard se touchent.  
  
 ![Texte utilisant des ligatures standard OpenType avec Palatino Linotype](./media/opentype-font-features/opentype-standard-ligatures-palatino.gif "Texte utilisant des ligatures standard OpenType avec Palatino Linotype")

 Vous pouvez cependant désactiver les fonctionnalités de ligature standard de sorte qu’une ligature standard comme « ff » s’affiche comme deux glyphes distincts et non comme un glyphe de caractères combinés.  
  
 ![Texte utilisant des ligatures standard OpenType désactivées](./media/opentype-font-features/disabled-opentype-standard-ligatures.gif "Texte utilisant des ligatures standard OpenType désactivées")  

 L’exemple de balisage suivant montre comment désactiver les glyphes standard de <xref:System.Windows.Documents.Typography> ligature pour la police Palatino Linotype, en utilisant les propriétés de l’objet.  
  
 [!code-xaml[OpenTypeFontSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#6)]  
  
<a name="swashes"></a>
## <a name="swashes"></a>Lettres ornées  
 Les lettres ornées sont des glyphes décoratifs qui utilisent une ornementation élaborée souvent associée à la calligraphie. Le texte suivant présente des glyphes standard et des glyphes à lettres ornées avec la police Pescadero.  
  
 ![Texte utilisant des glyphes standard et ornés OpenType](./media/opentype-font-features/opentype-standard-swash-glyphs.gif "Texte utilisant des glyphes standard et ornés OpenType")  

 Les lettres ornées sont souvent utilisés comme éléments décoratifs dans des expressions courtes annonçant par exemple un événement. Le texte suivant utilise des lettres ornées pour mettre en relief les majuscules du nom de l’événement.  
  
 ![Texte utilisant des lettres ornées OpenType](./media/opentype-font-features/opentype-swashes.gif "Texte utilisant des lettres ornées OpenType")  
  
 L’exemple de balisage suivant montre comment définir les <xref:System.Windows.Documents.Typography> lavages pour une police, en utilisant les propriétés de l’objet.  
  
 [!code-xaml[OpenTypeFontSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#7)]  
  
### <a name="contextual-swashes"></a>Lettres ornées contextuelles  
 Certaines combinaisons de glyphes à lettres ornées peuvent donner des résultats peu esthétiques, avec notamment le chevauchement de hampes descendantes dans les lettres adjacentes. En utilisant des lettres ornées contextuelles, vous pouvez obtenir un meilleur résultat visuel. Le texte suivant présente le même mot avant et après l’application d’une lettre ornée contextuelle.  
  
 ![Texte utilisant des lettres ornées contextuelles OpenType](./media/opentype-font-features/opentype-contextual-swashes.gif "Texte utilisant des glyphes ornés contextuels OpenType")  
  
 L’exemple de balisage suivant montre comment définir un swash contextuel <xref:System.Windows.Documents.Typography> pour la police Pescadero, en utilisant les propriétés de l’objet.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet16](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet16)]  
  
<a name="alternates"></a>
## <a name="alternates"></a>Alternatives  
 Les alternatives sont des glyphes qui peuvent être remplacés par un glyphe standard. Les polices OpenType, telles que la police Périclès utilisée dans les exemples suivants, peuvent contenir d’autres glyphes que vous pouvez utiliser pour créer différentes apparences pour le texte. Le texte suivant présente des glyphes standard avec la police Pericles.  
  
 ![Texte utilisant des glyphes standard OpenType](./media/opentype-font-features/opentype-standard-glyphs.gif "Texte utilisant des glyphes standard OpenType")  

 La police Pericles OpenType contient des glyphes supplémentaires qui fournissent des alternatives stylistiques à l’ensemble standard de glyphes. Le texte suivant présente des glyphes de style alternatif.  
  
 ![Texte utilisant des glyphes de style alternatifs OpenType](./media/opentype-font-features/opentype-stylistic-alternate-glyphs.gif "Texte utilisant des glyphes de style alternatifs OpenType")  
  
 L’exemple de balisage suivant montre comment définir les glyphes alternatifs <xref:System.Windows.Documents.Typography> stylistiques pour la police Périclès, en utilisant les propriétés de l’objet.  
  
 [!code-xaml[OpenTypeFontSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#2)]  
  
 Le texte suivant présente plusieurs autres glyphes de style alternatif pour la police Pericles.  
  
 ![Texte à l’aide de glyphes alternatifs stylistiques OpenType pour la police Périclès](./media/opentype-font-features/opentype-stylistic-alternate-glyphs-pericles.gif "Texte à l’aide de glyphes alternatifs stylistiques OpenType pour la police Périclès")

 L’exemple de balisage suivant montre comment définir ces autres glyphes de style alternatif.  
  
 [!code-xaml[OpenTypeFontSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#3)]  
  
### <a name="random-contextual-alternates"></a>Alternatives contextuelles aléatoires  
 Les alternatives contextuelles aléatoires proposent plusieurs glyphes de substitution pour un même caractère. Quand elle est implémentée avec des polices de caractères d’écriture, cette fonctionnalité peut simuler l’écriture manuscrite à partir d’un jeu de glyphes choisis de façon aléatoire avec de légères différences d’apparence. Le texte suivant présente des alternatives contextuelles aléatoires avec la police Lindsey. Notez que la lettre « a » présente de légères variations.  
  
 ![Texte utilisant des alternatives contextuelles aléatoires OpenType](./media/opentype-font-features/opentype-random-contextual-alternates.gif "Texte utilisant des alternatives contextuelles aléatoires OpenType")  
  
 L’exemple de balisage suivant montre comment définir des alternatives contextuelles aléatoires pour la police Lindsey, en utilisant les propriétés de l’objet. <xref:System.Windows.Documents.Typography>  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet20](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet20)]  
  
### <a name="historical-forms"></a>Formes historiques  
 Les formes historiques sont des conventions typographiques qui étaient courantes dans le passé. Dans le texte, l’expression « Boston, Massachusetts » présente une forme historique de glyphes avec la police Palatino Linotype.  
  
 ![Texte utilisant des formes historiques OpenType](./media/opentype-font-features/opentype-historical-forms.gif "Texte utilisant des formes historiques OpenType")  

 L’exemple de balisage suivant montre comment définir les formes historiques <xref:System.Windows.Documents.Typography> pour la police Palatino Linotype, en utilisant les propriétés de l’objet.  
  
 [!code-xaml[OpenTypeFontSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#8)]  
  
<a name="numerical_styles"></a>
## <a name="numerical-styles"></a>Styles numériques  
 Les polices OpenType prennent en charge un grand nombre de fonctionnalités qui peuvent être utilisées avec des valeurs numériques dans du texte.  
  
### <a name="fractions"></a>Fractions  
 OpenType polices de soutien styles pour les fractions, y compris coupé et empilés.  
  
 Le texte suivant présente des styles de fraction avec la police Palatino Linotype.  
  
 ![Texte utilisant des fractions OpenType avec barres obliques et barres horizontales](./media/opentype-font-features/opentype-slashed-stacked-fractions.gif "Texte utilisant des fractions OpenType avec barres obliques et barres horizontales")  

 L’exemple de balisage suivant montre comment définir les styles fractionnés pour la police Palatino Linotype, en utilisant les propriétés de l’objet. <xref:System.Windows.Documents.Typography>  
  
 [!code-xaml[OpenTypeFontSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#10)]  
  
### <a name="old-style-numerals"></a>Chiffres de style ancien  
 Les polices OpenType prennent en charge un format numérique à l’ancienne. Ce format est utile pour présenter les chiffres dans des styles qui ne sont plus courants. Le texte suivant présente une date du 18e siècle dans des formats numériques de style ancien avec la police Palatino Linotype.  
  
 ![Texte utilisant les chiffres OpenType de style ancien](./media/opentype-font-features/opentype-old-style-numerals.gif "Texte utilisant les chiffres OpenType de style ancien")  

 Le texte suivant présente des chiffres standard avec la police Palatino Linotype, suivis de chiffres de style ancien.  
  
 ![Texte utilisant les jeux de chiffres OpenType de style ancien](./media/opentype-font-features/opentype-old-style-numeral-sets.gif "Texte utilisant les jeux de chiffres OpenType de style ancien")  
  
 L’exemple de balisage suivant montre comment définir les chiffres de style ancien <xref:System.Windows.Documents.Typography> pour la police Palatino Linotype, en utilisant les propriétés de l’objet.  
  
 [!code-xaml[OpenTypeFontSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#11)]  
  
### <a name="proportional-and-tabular-figures"></a>Chiffres proportionnels et tabulaires  
 Les polices OpenType prennent en charge une caractéristique proportionnelle et tabulaire pour contrôler l’alignement des largeurs lors de l’utilisation des chiffres. Les chiffres proportionnels sont considérés comme ayant chacun une largeur différente (« 1 » est plus étroit que « 5 »). À l’inverse, les chiffres tabulaires sont considérés comme ayant la même largeur, ce qui permet de les aligner verticalement et d’améliorer leur lisibilité dans les documents financiers.  
  
 Le texte ci-dessous présente deux chiffres proportionnels dans la première colonne avec la police Miramonte. Comme vous pouvez le constater, les chiffres « 5 » et « 1 » n’ont pas la même largeur. La deuxième colonne présente ces deux mêmes valeurs numériques avec des largeurs ajustées au moyen de la fonctionnalité des chiffres tabulaires.  
  
 ![Texte utilisant les chiffres tabulaires et proportionnels OpenType](./media/opentype-font-features/opentype-proportional-tabular-figures.gif "Texte utilisant les chiffres tabulaires et proportionnels OpenType")  

 L’exemple de balisage suivant montre comment définir les figures proportionnelles <xref:System.Windows.Documents.Typography> et tabulaires pour la police Miramonte, en utilisant les propriétés de l’objet.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet19](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/Window1.xaml#opentypefontsnippet19)]  
  
### <a name="slashed-zero"></a>Zéro barré  
 Les polices OpenType prennent en charge un format zéro chiffre réduit pour souligner la différence entre la lettre « O » et le chiffre « 0 ». Le chiffre zéro barré est souvent utilisé pour les identificateurs dans les informations financières et commerciales.  
  
 Le texte suivant présente un exemple d’identificateur de commande avec la police Miramonte. La première ligne contient des chiffres standard. La deuxième ligne contient des chiffres zéro barré pour mieux les distinguer de la lettre « O » majuscule.  
  
 ![Texte utilisant des chiffres zéro barré OpenType](./media/opentype-font-features/opentype-slashed-zero-numerals.gif "Texte utilisant des chiffres zéro barré OpenType")  

 L’exemple de balisage suivant montre comment définir les chiffres zéro réduits <xref:System.Windows.Documents.Typography> pour la police Miramonte, en utilisant les propriétés de l’objet.  
  
 [!code-xaml[OpenTypeFontSamples#OpenTypeFontSnippet15](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#opentypefontsnippet15)]  
  
<a name="typography_class"></a>
## <a name="typography-class"></a>Classe Typography  
 L’objet <xref:System.Windows.Documents.Typography> expose l’ensemble des fonctionnalités qu’une police OpenType prend en charge. En définissant <xref:System.Windows.Documents.Typography> les propriétés de la majoration, vous pouvez facilement écrire des documents qui tirent parti des fonctionnalités OpenType.  
  
 Le texte suivant présente des majuscules standard avec la police Pescadero, suivies de lettres de type « SmallCaps » et « AllSmallCaps ». Dans ce cas, la taille de police utilisée est identique pour les trois mots.  
  
 ![Texte utilisant des majuscules OpenType](./media/opentype-font-features/opentype-capitals.gif "Texte utilisant des majuscules OpenType")  

 L’exemple de balisage suivant montre comment définir les majuscules pour la police Pescadero, en utilisant les propriétés de l’objet. <xref:System.Windows.Documents.Typography> Quand le format « SmallCaps » est utilisé, les majuscules de début sont ignorées.  
  
 [!code-xaml[OpenTypeFontSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontSamples/CS/PageOne.xaml#9)]  
  
 L’exemple de code suivant effectue la même tâche que l’exemple de balisage précédent.  
  
 [!code-csharp[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/TypographyCodeSnippets/CSharp/Page1.xaml.cs#typographycodesnippet1)]
 [!code-vb[TypographyCodeSnippets#TypographyCodeSnippet1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TypographyCodeSnippets/visualbasic/page1.xaml.vb#typographycodesnippet1)]  
  
### <a name="typography-class-properties"></a>Propriétés de la classe Typography  
 Le tableau suivant répertorie les propriétés, les valeurs et les paramètres par défaut de l’objet. <xref:System.Windows.Documents.Typography>  
  
|Propriété|Valeur(s)|Valeur par défaut|  
|--------------|----------------|-------------------|  
|<xref:System.Windows.Documents.Typography.AnnotationAlternates%2A>|Valeur numérique - octet|0|  
|<xref:System.Windows.Documents.Typography.Capitals%2A>|<xref:System.Windows.FontCapitals.AllPetiteCaps>&#124; <xref:System.Windows.FontCapitals.AllSmallCaps> &#124; &#124; <xref:System.Windows.FontCapitals.Normal> &#124; <xref:System.Windows.FontCapitals.PetiteCaps> &#124; &#124; &#124; <xref:System.Windows.FontCapitals.Titling> <xref:System.Windows.FontCapitals.SmallCaps><xref:System.Windows.FontCapitals.Unicase>|<xref:System.Windows.FontCapitals.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.CapitalSpacing%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.CaseSensitiveForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.ContextualAlternates%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.ContextualSwashes%2A>|Valeur numérique - octet|0|  
|<xref:System.Windows.Documents.Typography.DiscretionaryLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianExpertForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.EastAsianLanguage%2A>|<xref:System.Windows.FontEastAsianLanguage.HojoKanji><xref:System.Windows.FontEastAsianLanguage.Jis04> &#124; &#124; <xref:System.Windows.FontEastAsianLanguage.Jis78> &#124; <xref:System.Windows.FontEastAsianLanguage.Jis83> &#124; &#124; <xref:System.Windows.FontEastAsianLanguage.Jis90> &#124; <xref:System.Windows.FontEastAsianLanguage.NlcKanji> &#124; <xref:System.Windows.FontEastAsianLanguage.Normal> &#124; <xref:System.Windows.FontEastAsianLanguage.Simplified> &#124; &#124; <xref:System.Windows.FontEastAsianLanguage.Traditional><xref:System.Windows.FontEastAsianLanguage.TraditionalNames>|<xref:System.Windows.FontEastAsianLanguage.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.EastAsianWidths%2A>|<xref:System.Windows.FontEastAsianWidths.Full>&#124; <xref:System.Windows.FontEastAsianWidths.Half> &#124; <xref:System.Windows.FontEastAsianWidths.Normal> &#124; &#124; <xref:System.Windows.FontEastAsianWidths.Proportional> &#124; &#124; <xref:System.Windows.FontEastAsianWidths.Quarter><xref:System.Windows.FontEastAsianWidths.Third>|<xref:System.Windows.FontEastAsianWidths.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.Fraction%2A>|<xref:System.Windows.FontFraction.Normal> &#124; <xref:System.Windows.FontFraction.Slashed> &#124; <xref:System.Windows.FontFraction.Stacked>|<xref:System.Windows.FontFraction.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.HistoricalForms%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.HistoricalLigatures%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Kerning%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.MathematicalGreek%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.NumeralAlignment%2A>|<xref:System.Windows.FontNumeralAlignment.Normal> &#124; <xref:System.Windows.FontNumeralAlignment.Proportional> &#124; <xref:System.Windows.FontNumeralAlignment.Tabular>|<xref:System.Windows.FontNumeralAlignment.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.NumeralStyle%2A>|<xref:System.Boolean>|<xref:System.Windows.FontNumeralStyle.Normal?displayProperty=nameWithType>|  
|<xref:System.Windows.Documents.Typography.SlashedZero%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StandardLigatures%2A>|<xref:System.Boolean>|`true`|  
|<xref:System.Windows.Documents.Typography.StandardSwashes%2A>|Valeur numérique - octet|0|  
|<xref:System.Windows.Documents.Typography.StylisticAlternates%2A>|Valeur numérique - octet|0|  
|<xref:System.Windows.Documents.Typography.StylisticSet1%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet2%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet3%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet4%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet5%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet6%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet7%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet8%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet9%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet10%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet11%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet12%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet13%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet14%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet15%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet16%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet17%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet18%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet19%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.StylisticSet20%2A>|<xref:System.Boolean>|`false`|  
|<xref:System.Windows.Documents.Typography.Variants%2A>|<xref:System.Windows.FontVariants.Inferior>&#124; <xref:System.Windows.FontVariants.Normal> &#124; <xref:System.Windows.FontVariants.Ordinal> &#124; &#124; <xref:System.Windows.FontVariants.Ruby> &#124; &#124; <xref:System.Windows.FontVariants.Subscript><xref:System.Windows.FontVariants.Superscript>|<xref:System.Windows.FontVariants.Normal?displayProperty=nameWithType>|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Documents.Typography>
- [Spécification OpenType](https://docs.microsoft.com/typography/opentype/spec/)
- [Typographie dans WPF](typography-in-wpf.md)
- [Exemple de pack de polices OpenType](sample-opentype-font-pack.md)
- [Empaquetage de polices avec des applications](packaging-fonts-with-applications.md)
