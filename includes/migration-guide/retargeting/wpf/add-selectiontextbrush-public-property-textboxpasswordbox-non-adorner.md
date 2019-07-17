---
ms.openlocfilehash: 01bbc49cb0febc5a29dafc7c311b848387a4094a
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803549"
---
### <a name="add-selectiontextbrush-public-property-to-textboxpasswordbox-non-adorner-selection"></a>Ajout de la propriété publique SelectionTextBrush à la sélection sans ornement pour TextBox/PasswordBox

|   |   |
|---|---|
|Détails|Dans les applications WPF utilisant la [sélection de texte sans ornement](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-TextBox-PasswordBox-text-selection-does-not-follow-system-colors.md) pour <xref:System.Windows.Controls.TextBox> et <xref:System.Windows.Controls.PasswordBox>, les développeurs peuvent maintenant définir la propriété SelectionTextBrush récemment ajoutée afin de modifier le rendu du texte sélectionné.  Par défaut, cette couleur change avec <xref:System.Windows.SystemColors.HighlightTextBrushKey>.  Si la sélection de texte sans ornement n’est pas activée, cette propriété ne fait rien.|
|Suggestion|Une fois que la sélection de texte sans ornement est activée, vous pouvez utiliser la propriété <xref:System.Windows.Controls.PasswordBox.SelectionTextBrush?displayProperty=nameWithType> et <xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush> pour changer l’apparence du texte sélectionné. Pour ce faire, vous pouvez utiliser XAML :<pre><code class="lang-xaml">&lt;TextBox SelectionBrush=&quot;Red&quot; SelectionTextBrush=&quot;White&quot;  SelectionOpacity=&quot;0.5&quot;&#13;&#10;Foreground=&quot;Blue&quot; CaretBrush=&quot;Blue&quot;&gt;&#13;&#10;This is some text.&#13;&#10;&lt;/TextBox&gt;&#13;&#10;</code></pre>|
|Portée|Majeur|
|Version|4.8|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrushProperty?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.Primitives.TextBoxBase.SelectionTextBrush?displayProperty=nameWithType></li><li>[System.Windows.Controls.TextBox](xref:System.Windows.Controls.TextBox)</li><li>[System.Windows.Controls.PasswordBox](xref:System.Windows.Controls.PasswordBox)</li></ul>|

