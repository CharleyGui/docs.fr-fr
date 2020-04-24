---
title: Validation des entrées de l’utilisateur
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, validating user input
- validation [Windows Forms], Windows Forms user input
- user input [Windows Forms], validating in Windows Forms
- validating user input [Windows Forms], Windows Forms
ms.assetid: 4ec07681-1dee-4bf9-be5e-718f635a33a1
ms.openlocfilehash: eafbf54552566011fef9d2dbeb5e9f9fa3facabd
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646304"
---
# <a name="user-input-validation-in-windows-forms"></a>Validation des entrées d’utilisateur dans les Windows Forms
Lorsque les utilisateurs saisissent des données dans votre application, vous pouvez vérifier que les données sont valides avant que votre application ne les utilise. Vous pouvez exiger que certains champs de texte ne soient pas de longueur nulle, qu’un champ soit formaté comme numéro de téléphone ou autre type de données bien formées, ou qu’une chaîne ne contienne aucun caractère dangereux qui pourrait être utilisé pour compromettre la sécurité d’une base de données. Windows Forms vous permet de valider l’entrée de votre application.  
  
## <a name="validation-with-the-maskedtextbox-control"></a>Validation avec le contrôle MaskedTextBox  
 Si vous devez exiger des utilisateurs qu’ils saisissent des données dans un format bien défini, comme un <xref:System.Windows.Forms.MaskedTextBox> numéro de téléphone ou un numéro de pièce, vous pouvez l’accomplir rapidement et avec un code minimal en utilisant le contrôle. Un *masque* est une chaîne composée de caractères à partir d’un langage masquant qui spécifie quels caractères peuvent être entrés à n’importe quelle position donnée dans la boîte de texte. Le contrôle affiche un ensemble d’invites à l’utilisateur. Si l’utilisateur tape une entrée incorrecte, par exemple, l’utilisateur tape une lettre lorsqu’un chiffre est requis, le contrôle rejette automatiquement l’entrée.  
  
 Le langage masquant <xref:System.Windows.Forms.MaskedTextBox> qui est utilisé par est très flexible. Il vous permet de spécifier les caractères requis, les personnages optionnels, les caractères littéral, tels que les traits d’union et les parenthèses, les caractères de devises et les séparateurs de date. Le contrôle fonctionne également bien lorsqu’il est lié à une source de données. L’événement <xref:System.Windows.Forms.Binding.Format> sur une liaison de données peut être utilisé pour <xref:System.Windows.Forms.Binding.Parse> reformer les données entrantes pour se conformer au masque, et l’événement peut être utilisé pour reformer les données sortantes pour se conformer aux spécifications du champ de données.  
  
 Pour plus d’informations, voir [MaskedTextBox Control](./controls/maskedtextbox-control-windows-forms.md).  
  
## <a name="event-driven-validation"></a>Validation axée sur l’événement  
 Si vous souhaitez un contrôle programmatique complet sur la validation ou si vous devez effectuer des vérifications de validation complexes, vous devez utiliser les événements de validation intégrés à la plupart des contrôles Windows Forms. Chaque contrôle qui accepte l’entrée <xref:System.Windows.Forms.Control.Validating> gratuite de l’utilisateur a un événement qui se produira chaque fois que le contrôle nécessite une validation des données. Dans <xref:System.Windows.Forms.Control.Validating> la méthode de traitement des événements, vous pouvez valider l’entrée de l’utilisateur de plusieurs façons. Par exemple, si vous avez une boîte de texte qui doit contenir un code postal, vous pouvez effectuer la validation de la manière suivante :  
  
- Si le code postal doit appartenir à un groupe spécifique de codes postaux, vous pouvez effectuer une comparaison de chaînes sur l’entrée pour valider les données saisies par l’utilisateur. Par exemple, si le code postal doit figurer dans l’ensemble '10001, 10002, 10003', alors vous pouvez utiliser une comparaison de chaînes pour valider les données.  
  
- Si le code postal doit être sous une forme spécifique, vous pouvez utiliser des expressions régulières pour valider les données saisies par l’utilisateur. Par exemple, pour `#####` valider le formulaire `#####-####`ou `^(\d{5})(-\d{4})?$`, vous pouvez utiliser l’expression régulière . Pour valider `A#A #A#`le formulaire, vous `[A-Z]\d[A-Z] \d[A-Z]\d`pouvez utiliser l’expression régulière . Pour plus d’informations sur les expressions régulières, voir [.NET Framework Expressions régulières](../../standard/base-types/regular-expressions.md) et [exemples d’expression régulière](../../standard/base-types/regular-expression-example-scanning-for-hrefs.md).  
  
- Si le code postal doit être un code postal valide des États-Unis, vous pouvez appeler un service Web de code postal pour valider les données saisies par l’utilisateur.  
  
 L’événement <xref:System.Windows.Forms.Control.Validating> est fourni <xref:System.ComponentModel.CancelEventArgs>un objet de type . Si vous déterminez que les données du contrôle <xref:System.Windows.Forms.Control.Validating> ne sont pas valides, vous pouvez annuler l’événement en définissant la propriété de <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> cet objet à `true`. Si vous ne <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> définissez pas la propriété, Windows Forms suppose <xref:System.Windows.Forms.Control.Validated> que la validation a réussi pour ce contrôle, et augmenter l’événement.  
  
 Pour un exemple de code qui <xref:System.Windows.Controls.TextBox>valide <xref:System.Windows.Forms.Control.Validating>une adresse e-mail dans un , voir .  
  
### <a name="data-binding-and-event-driven-validation"></a>Liaison de données et validation axée sur les événements  
 La validation est très utile lorsque vous avez lié vos contrôles à une source de données, comme une table de base de données. En utilisant la validation, vous pouvez vous assurer que les données de votre contrôle satisfont au format requis par la source de données, et qu’elles ne contiennent pas de caractères spéciaux tels que des guillemets et des barres obliques arrière qui pourraient être dangereuses.  
  
 Lorsque vous utilisez la liaison de données, les données de votre <xref:System.Windows.Forms.Control.Validating> contrôle sont synchronisées avec la source de données lors de l’exécution de l’événement. Si vous <xref:System.Windows.Forms.Control.Validating> annulez l’événement, les données ne seront pas synchronisées avec la source de données.  
  
> [!IMPORTANT]
> Si vous avez une validation <xref:System.Windows.Forms.Control.Validating> personnalisée qui a lieu après l’événement, elle n’affectera pas la liaison des données. Par exemple, si vous <xref:System.Windows.Forms.Control.Validated> avez du code dans un cas où il tente d’annuler la liaison de données, la liaison de données se produira toujours. Dans ce cas, pour <xref:System.Windows.Forms.Control.Validated> effectuer la validation dans l’événement, modifier la propriété de **mode de mise à jour de source de données** du contrôle **(sous (Databindings)**\\ **(Advanced)**) de **OnValidation** à **Jamais**, et ajouter *Control*`.DataBindings["`*\<YOURFIELD>* `"].WriteValue()` à votre code de validation.  
  
### <a name="implicit-and-explicit-validation"></a>Validation implicite et explicite  
 Alors, quand les données d’un contrôle sont-elles validées ? C’est à vous, le développeur. Vous pouvez utiliser une validation implicite ou explicite, selon les besoins de votre application.  
  
#### <a name="implicit-validation"></a>Validation implicite  
 L’approche de validation implicite valide les données au fur et à mesure que l’utilisateur y entre. Vous pouvez valider les données au fur et à mesure que les données sont saisies dans un contrôle en lisant les clés lorsqu’elles sont pressées, ou plus généralement chaque fois que l’utilisateur éloigne l’accent d’entrée d’un contrôle et se déplace vers l’autre. Cette approche est utile lorsque vous souhaitez donner à l’utilisateur des commentaires immédiats sur les données pendant qu’ils fonctionnent.  
  
 Si vous souhaitez utiliser la validation implicite pour un <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> contrôle, <xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange> <xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>vous devez définir la propriété de ce contrôle à ou . Si vous <xref:System.Windows.Forms.Control.Validating> annulez l’événement, le comportement du contrôle sera <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>déterminé par la valeur que vous avez assignée à . Si vous <xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange>avez assigné, l’annulation de l’événement entraînera l’événement <xref:System.Windows.Forms.Control.Validated> de ne pas se produire. L’accent sur l’entrée restera sur le contrôle actuel jusqu’à ce que l’utilisateur modifie les données en une entrée valide. Si vous <xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>avez <xref:System.Windows.Forms.Control.Validated> attribué, l’événement ne se produira pas lorsque vous annulez l’événement, mais la mise au point sera toujours changer pour le prochain contrôle.  
  
 L’attribution <xref:System.Windows.Forms.AutoValidate.Disable> <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> à la propriété empêche complètement la validation implicite. Pour valider vos contrôles, vous devrez utiliser une validation explicite.  
  
#### <a name="explicit-validation"></a>Validation explicite  
 L’approche de validation explicite valide les données en même temps. Vous pouvez valider les données en réponse à une action de l’utilisateur, comme cliquer sur un bouton Enregistrer ou un lien Suivant. Lorsque l’action utilisateur se produit, vous pouvez déclencher une validation explicite de l’une des façons suivantes :  
  
- Appelez <xref:System.Windows.Forms.ContainerControl.Validate%2A> pour valider le dernier contrôle pour avoir perdu la mise au point.  
  
- Appelez <xref:System.Windows.Forms.ContainerControl.ValidateChildren%2A> pour valider tous les contrôles de l’enfant sous forme ou contrôle de conteneurs.  
  
- Appelez manuellement une méthode personnalisée pour valider manuellement les données dans les contrôles.  
  
#### <a name="default-implicit-validation-behavior-for-windows-forms-controls"></a>Comportement de validation implicite par défaut pour les contrôles des formulaires Windows  
 Différents contrôles De formulaires Windows <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> ont des défauts différents pour leur propriété. Le tableau suivant affiche les contrôles les plus courants et leurs défauts.  
  
|Control|Comportement de validation par défaut|  
|-------------|---------------------------------|  
|<xref:System.Windows.Forms.ContainerControl>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
|<xref:System.Windows.Forms.PropertyGrid>|Propriété non exposée dans Visual Studio|  
|<xref:System.Windows.Forms.ToolStripContainer>|Propriété non exposée dans Visual Studio|  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
  
## <a name="closing-the-form-and-overriding-validation"></a>Fermeture du formulaire et validation absolue  
 Lorsqu’un contrôle maintient la mise au point parce que les données qu’il contient sont invalides, il est impossible de fermer la forme parente de l’une des façons habituelles :  
  
- En cliquant sur le bouton **Close.**  
  
- En sélectionnant **Close** dans le menu **Système.**  
  
- En appelant <xref:System.Windows.Forms.Form.Close%2A> la méthode programmatiquement.  
  
 Toutefois, dans certains cas, vous pouvez laisser l’utilisateur fermer le formulaire, que les valeurs des contrôles soient valides ou non. Vous pouvez remplacer la validation et fermer un formulaire qui contient encore <xref:System.Windows.Forms.Form.FormClosing> des données invalides en créant un gestionnaire pour l’événement du formulaire. Dans le cas, <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> définissez la propriété à `false`. Cela force la forme à fermer. Pour plus d'informations et pour obtenir un exemple, consultez <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>.  
  
> [!NOTE]
> Si vous forcez le formulaire à fermer de cette manière, toutes les données dans les contrôles du formulaire qui n’ont pas déjà été enregistrées sont perdues. En outre, les formulaires modaux ne valident pas le contenu des contrôles lorsqu’ils sont fermés. Vous pouvez toujours utiliser la validation de contrôle pour verrouiller la mise au point à un contrôle, mais vous n’avez pas à être préoccupé par le comportement associé à la fermeture du formulaire.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Control.Validating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>
- <xref:System.Windows.Forms.FormClosingEventArgs?displayProperty=nameWithType>
- [MaskedTextBox, contrôle](./controls/maskedtextbox-control-windows-forms.md)
- [Exemples d'expressions régulières](../../standard/base-types/regular-expression-example-scanning-for-hrefs.md)
