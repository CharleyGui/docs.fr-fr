---
title: Validation des entrées d’utilisateur
description: Découvrez les différentes façons dont vous pouvez utiliser Windows Forms pour valider l’entrée d’utilisateur dans vos applications.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, validating user input
- validation [Windows Forms], Windows Forms user input
- user input [Windows Forms], validating in Windows Forms
- validating user input [Windows Forms], Windows Forms
ms.assetid: 4ec07681-1dee-4bf9-be5e-718f635a33a1
ms.openlocfilehash: 89f245a523d473f052a337d8f29c2c05105d75eb
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325557"
---
# <a name="user-input-validation-in-windows-forms"></a>Validation des entrées d’utilisateur dans les Windows Forms
Lorsque les utilisateurs entrent des données dans votre application, vous pouvez vérifier que les données sont valides avant que votre application ne l’utilise. Vous pouvez exiger que certains champs de texte ne soient pas de longueur nulle, qu’un champ soit mis en forme comme un numéro de téléphone ou un autre type de données bien formées, ou qu’une chaîne ne contienne pas de caractères non sécurisés susceptibles d’être utilisés pour compromettre la sécurité d’une base de données. Windows Forms offre plusieurs méthodes pour valider l’entrée dans votre application.  
  
## <a name="validation-with-the-maskedtextbox-control"></a>Validation avec le contrôle MaskedTextBox  
 Si vous devez demander aux utilisateurs d’entrer des données dans un format bien défini, tel qu’un numéro de téléphone ou un numéro de référence, vous pouvez le faire rapidement et avec un minimum de code en utilisant le <xref:System.Windows.Forms.MaskedTextBox> contrôle. Un *masque* est une chaîne composée de caractères issus d’un langage de masquage qui spécifie les caractères qui peuvent être entrés à une position donnée dans la zone de texte. Le contrôle affiche un ensemble d’invites à l’utilisateur. Si l’utilisateur tape une entrée incorrecte, par exemple, l’utilisateur tape une lettre quand un chiffre est requis, le contrôle rejette automatiquement l’entrée.  
  
 Le langage de masquage utilisé par <xref:System.Windows.Forms.MaskedTextBox> est très flexible. Elle vous permet de spécifier des caractères obligatoires, des caractères facultatifs, des caractères littéraux, tels que des traits d’Union et des parenthèses, des caractères monétaires et des séparateurs de date. Le contrôle fonctionne également bien lorsqu’il est lié à une source de données. L' <xref:System.Windows.Forms.Binding.Format> événement sur une liaison de données peut être utilisé pour reformater les données entrantes pour se conformer au masque, et l' <xref:System.Windows.Forms.Binding.Parse> événement peut être utilisé pour reformater les données sortantes de façon à ce qu’elles soient conformes aux spécifications du champ de données.  
  
 Pour plus d’informations, consultez [MaskedTextBox Control](./controls/maskedtextbox-control-windows-forms.md).  
  
## <a name="event-driven-validation"></a>Validation pilotée par les événements  
 Si vous souhaitez un contrôle total de la validation par programmation ou si vous devez effectuer des contrôles de validation complexes, vous devez utiliser les événements de validation intégrés à la plupart des contrôles Windows Forms. Chaque contrôle qui accepte les entrées utilisateur de forme libre a un <xref:System.Windows.Forms.Control.Validating> événement qui se produit chaque fois que le contrôle requiert la validation des données. Dans la <xref:System.Windows.Forms.Control.Validating> méthode de gestion des événements, vous pouvez valider l’entrée utilisateur de plusieurs façons. Par exemple, si vous avez une zone de texte qui doit contenir un code postal, vous pouvez effectuer la validation des manières suivantes :  
  
- Si le code postal doit appartenir à un groupe spécifique de codes postaux, vous pouvez effectuer une comparaison de chaînes sur l’entrée pour valider les données entrées par l’utilisateur. Par exemple, si le code postal doit se trouver dans le jeu {10001, 10002, 10003}, vous pouvez utiliser une comparaison de chaînes pour valider les données.  
  
- Si le code postal doit être dans un formulaire spécifique, vous pouvez utiliser des expressions régulières pour valider les données entrées par l’utilisateur. Par exemple, pour valider le formulaire `#####` ou `#####-####` , vous pouvez utiliser l’expression régulière `^(\d{5})(-\d{4})?$` . Pour valider le formulaire `A#A #A#` , vous pouvez utiliser l’expression régulière `[A-Z]\d[A-Z] \d[A-Z]\d` . Pour plus d’informations sur les expressions régulières, consultez [.NET Framework des expressions](../../standard/base-types/regular-expressions.md) régulières et des exemples d’expressions [régulières](../../standard/base-types/regular-expression-example-scanning-for-hrefs.md).  
  
- Si le code postal doit être un code postal États-Unis valide, vous pouvez appeler un service Web de code postal pour valider les données entrées par l’utilisateur.  
  
 L' <xref:System.Windows.Forms.Control.Validating> événement est fourni avec un objet de type <xref:System.ComponentModel.CancelEventArgs> . Si vous déterminez que les données du contrôle ne sont pas valides, vous pouvez annuler l' <xref:System.Windows.Forms.Control.Validating> événement en affectant à la propriété de cet objet la valeur <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> `true` . Si vous ne définissez pas la <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> propriété, Windows Forms supposera que la validation a réussi pour ce contrôle et déclenchera l' <xref:System.Windows.Forms.Control.Validated> événement.  
  
 Pour obtenir un exemple de code qui valide une adresse de messagerie dans un <xref:System.Windows.Controls.TextBox> , consultez <xref:System.Windows.Forms.Control.Validating> .  
  
### <a name="data-binding-and-event-driven-validation"></a>Liaison de données et validation pilotée par les événements  
 La validation est très utile lorsque vous avez lié vos contrôles à une source de données, telle qu’une table de base de données. À l’aide de la validation, vous pouvez vous assurer que les données de votre contrôle respectent le format requis par la source de données, et qu’il ne contient pas de caractères spéciaux tels que des guillemets et des barres obliques inverses qui peuvent ne pas être sécurisés.  
  
 Lorsque vous utilisez la liaison de données, les données de votre contrôle sont synchronisées avec la source de données pendant l’exécution de l' <xref:System.Windows.Forms.Control.Validating> événement. Si vous annulez l' <xref:System.Windows.Forms.Control.Validating> événement, les données ne seront pas synchronisées avec la source de données.  
  
> [!IMPORTANT]
> Si vous avez une validation personnalisée qui a lieu après l' <xref:System.Windows.Forms.Control.Validating> événement, elle n’affecte pas la liaison de données. Par exemple, si vous avez du code dans un <xref:System.Windows.Forms.Control.Validated> événement qui tente d’annuler la liaison de données, la liaison de données sera toujours effectuée. Dans ce cas, pour effectuer la validation dans l' <xref:System.Windows.Forms.Control.Validated> événement, modifiez la propriété **mode de mise à jour** de la source de données du contrôle (**sous (DataBindings)** \\ **(avancé**)) de **OnValidation** à **Never**, puis ajoutez le *contrôle* `.DataBindings["` *\<YOURFIELD>* `"].WriteValue()` à votre code de validation.  
  
### <a name="implicit-and-explicit-validation"></a>Validation implicite et explicite  
 Quand les données d’un contrôle sont-elles validées ? C’est à vous, le développeur. Vous pouvez utiliser une validation implicite ou explicite, selon les besoins de votre application.  
  
#### <a name="implicit-validation"></a>Validation implicite  
 L’approche de validation implicite valide les données au fur et à mesure que l’utilisateur les entre. Vous pouvez valider les données au fur et à mesure que les données sont entrées dans un contrôle en lisant les touches au fur et à mesure qu’elles sont enfoncées, ou plus souvent chaque fois que l’utilisateur éloigne le focus d’entrée d’un contrôle et passe au suivant. Cette approche est utile lorsque vous souhaitez fournir à l’utilisateur des commentaires immédiats sur les données au fur et à mesure de leur travail.  
  
 Si vous souhaitez utiliser la validation implicite pour un contrôle, vous devez affecter à la propriété de ce contrôle la valeur <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> <xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange> ou <xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange> . Si vous annulez l' <xref:System.Windows.Forms.Control.Validating> événement, le comportement du contrôle est déterminé par la valeur que vous avez assignée à <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> . Si vous l’avez affecté <xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange> , l’annulation de l’événement entraînera la non-exécution de l' <xref:System.Windows.Forms.Control.Validated> événement. Le focus d’entrée reste sur le contrôle actuel jusqu’à ce que l’utilisateur modifie les données en une entrée valide. Si vous l’avez affecté <xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange> , l' <xref:System.Windows.Forms.Control.Validated> événement ne se produit pas quand vous annulez l’événement, mais le focus reste toujours sur le contrôle suivant.  
  
 L’assignation <xref:System.Windows.Forms.AutoValidate.Disable> à la <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> propriété empêche entièrement la validation implicite. Pour valider vos contrôles, vous devez utiliser la validation explicite.  
  
#### <a name="explicit-validation"></a>Validation explicite  
 L’approche de validation explicite valide les données à un moment donné. Vous pouvez valider les données en réponse à une action de l’utilisateur, par exemple en cliquant sur un bouton enregistrer ou sur un lien suivant. Lorsque l’action de l’utilisateur se produit, vous pouvez déclencher la validation explicite de l’une des manières suivantes :  
  
- Appelez <xref:System.Windows.Forms.ContainerControl.Validate%2A> pour valider le dernier contrôle qui a perdu le focus.  
  
- Appelez <xref:System.Windows.Forms.ContainerControl.ValidateChildren%2A> pour valider tous les contrôles enfants dans un formulaire ou un contrôle conteneur.  
  
- Appelez une méthode personnalisée pour valider les données dans les contrôles manuellement.  
  
#### <a name="default-implicit-validation-behavior-for-windows-forms-controls"></a>Comportement de validation implicite par défaut pour les contrôles Windows Forms  
 Les différents contrôles de Windows Forms ont des valeurs par défaut différentes pour leur <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> propriété. Le tableau suivant présente les contrôles les plus courants et leurs valeurs par défaut.  
  
|Control|Comportement de validation par défaut|  
|-------------|---------------------------------|  
|<xref:System.Windows.Forms.ContainerControl>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
|<xref:System.Windows.Forms.PropertyGrid>|Propriété non exposée dans Visual Studio|  
|<xref:System.Windows.Forms.ToolStripContainer>|Propriété non exposée dans Visual Studio|  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
  
## <a name="closing-the-form-and-overriding-validation"></a>Fermeture du formulaire et substitution de la validation  
 Lorsqu’un contrôle gère le focus parce que les données qu’il contient ne sont pas valides, il est impossible de fermer le formulaire parent de l’une des manières habituelles :  
  
- En cliquant sur le bouton **Fermer** .  
  
- En sélectionnant **Fermer** dans le menu **système** .  
  
- En appelant la <xref:System.Windows.Forms.Form.Close%2A> méthode par programme.  
  
 Toutefois, dans certains cas, vous souhaiterez peut-être laisser l’utilisateur fermer le formulaire, que les valeurs des contrôles soient valides ou non. Vous pouvez substituer la validation et fermer un formulaire qui contient encore des données non valides en créant un gestionnaire pour l’événement du formulaire <xref:System.Windows.Forms.Form.FormClosing> . Dans l’événement, affectez <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> à la propriété la valeur `false` . Cela force la fermeture du formulaire. Pour plus d'informations et pour obtenir un exemple, consultez <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>.  
  
> [!NOTE]
> Si vous forcez le formulaire à se fermer de cette manière, toutes les données des contrôles du formulaire qui n’ont pas encore été enregistrées sont perdues. En outre, les formulaires modaux ne valident pas le contenu des contrôles lorsqu’ils sont fermés. Vous pouvez toujours utiliser la validation de contrôle pour verrouiller le focus sur un contrôle, mais vous n’avez pas à vous soucier du comportement associé à la fermeture du formulaire.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Control.Validating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>
- <xref:System.Windows.Forms.FormClosingEventArgs?displayProperty=nameWithType>
- [MaskedTextBox, contrôle](./controls/maskedtextbox-control-windows-forms.md)
- [Exemples d'expressions régulières](../../standard/base-types/regular-expression-example-scanning-for-hrefs.md)
