---
title: 'Procédure : convertir des entrées d’utilisateur numériques figurant dans des contrôles web en nombres'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- parsing strings [.NET Framework], numeric strings
- converting numeric user input to number
- numbers [.NET Framework], converting numeric user input to number
ms.assetid: f27ddfb8-7479-4b79-8879-02a3bd8402d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5af942b5e7576c13ff7be8d11c0009fd0c4f7462
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882467"
---
# <a name="how-to-convert-numeric-user-input-in-web-controls-to-numbers"></a>Procédure : convertir des entrées d’utilisateur numériques figurant dans des contrôles web en nombres
Étant donné qu’une page web peut être affichée n’importe où dans le monde, les utilisateurs peuvent entrer des données numériques dans un contrôle <xref:System.Web.UI.WebControls.TextBox> dans un nombre de formats pratiquement illimité. Il est par conséquent très important de déterminer les paramètres régionaux et la culture de l’utilisateur d’une page web. Après avoir analysé une entrée d’utilisateur, vous pouvez appliquer les conventions de mise en forme définies par les paramètres régionaux et la culture de l’utilisateur.  
  
### <a name="to-convert-numeric-input-from-a-web-textbox-control-to-a-number"></a>Pour convertir une entrée numérique d’un contrôle Web TextBox en nombre  
  
1. Déterminez si le tableau de chaînes retourné par la propriété <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> est rempli. Si ce n’est pas le cas, passez à l’étape 6.  
  
2. Si le tableau de chaînes retourné par la propriété <xref:System.Web.HttpRequest.UserLanguages%2A> est rempli, récupérez son premier élément. Le premier élément indique la langue et la région par défaut ou préférées de l’utilisateur.  
  
3. Instanciez un objet <xref:System.Globalization.CultureInfo> représentant la culture préférée de l’utilisateur en appelant le constructeur <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType>.  
  
4. Appelez la méthode `TryParse` ou `Parse` du type numérique dans lequel vous souhaitez convertir l’entrée de l’utilisateur. Utilisez une surcharge de la méthode `TryParse` ou `Parse` avec un paramètre `provider` et transférez-y l’un des éléments suivants :  
  
    - L’objet <xref:System.Globalization.CultureInfo> créé à l’étape 3  
  
    - L’objet <xref:System.Globalization.NumberFormatInfo> retourné par la propriété <xref:System.Globalization.CultureInfo.NumberFormat%2A> de l’objet <xref:System.Globalization.CultureInfo> créé à l’étape 3  
  
5. Si la conversion échoue, répétez les étapes 2 à 4 pour chaque élément restant dans le tableau de chaînes retourné par la propriété <xref:System.Web.HttpRequest.UserLanguages%2A>.  
  
6. Si la conversion échoue toujours ou si le tableau de chaînes retourné par la propriété <xref:System.Web.HttpRequest.UserLanguages%2A> est vide, analysez la chaîne à l’aide de la culture invariante retournée par la propriété <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre la page code-behind complète d’un formulaire Web qui invite l’utilisateur à entrer une valeur numérique dans un contrôle <xref:System.Web.UI.WebControls.TextBox> et la convertit en nombre. Ce nombre est ensuite doublé et affiché en appliquant les mêmes règles de mise en forme que l’entrée d’origine.  
  
 [!code-csharp[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/cs/NumericUserInput1.aspx.cs#1)]
 [!code-vb[Formatting.HowTo.ParseNumericInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseNumericInput/vb/NumericUserInput1.aspx.vb#1)]  
  
 La propriété <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> est remplie par les noms de la culture qui figurent dans les en-têtes `Accept-Language` inclus dans une requête HTTP. Toutefois, certains navigateurs n’incluent pas les en-têtes `Accept-Language` dans leurs demandes, et les utilisateurs peuvent également supprimer totalement ces en-têtes. Il est donc important de disposer d’une culture de secours quand vous analysez l’entrée de l’utilisateur. En général, la culture de secours est la culture invariante retournée par <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Les utilisateurs peuvent également fournir à Internet Explorer des noms de cultures qu’ils entrent dans une zone de texte, avec la possibilité que ces noms de cultures ne soient pas valides. Il est donc important d’utiliser la gestion des exceptions quand vous instanciez un objet <xref:System.Globalization.CultureInfo>.  
  
 Quand il est extrait d’une requête HTTP soumise par Internet Explorer, le tableau <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> est rempli selon l’ordre de préférence de l’utilisateur. Le premier élément du tableau contient le nom de la culture/région principale de l’utilisateur. Si le tableau contient d’autres éléments, Internet Explorer leur assigne arbitrairement un spécificateur de qualité, séparé du nom de culture par un point virgule. Par exemple, une entrée pour la culture fr-FR peut prendre la forme `fr-FR;q=0.7`.  
  
 L’exemple appelle le constructeur <xref:System.Globalization.CultureInfo.%23ctor%2A> avec son paramètre `useUserOverride` défini sur `false` pour créer un nouvel objet <xref:System.Globalization.CultureInfo>. Cela garantit que, si le nom de la culture est le nom de la culture par défaut sur le serveur, le nouvel objet <xref:System.Globalization.CultureInfo> créé par le constructeur de classe contient les paramètres par défaut d’une culture et ne reflète pas les paramètres substitués en utilisant l’application **Options régionales et linguistiques du serveur**. Les valeurs des paramètres substitués sur le serveur sont peu susceptibles d’exister sur le système de l’utilisateur ou d’apparaître dans l’entrée de l’utilisateur.  
  
 Votre code peut appeler la méthode `Parse` ou `TryParse` du type numérique dans lequel sera convertie l’entrée de l’utilisateur. Des appels répétés à une méthode d’analyse peuvent être nécessaires pour une opération d’analyse unique. Par conséquent, la méthode `TryParse` est préférable, car elle retourne `false` si une opération d’analyse échoue. En revanche, la gestion d’exceptions répétées générées par la méthode `Parse` peut se révéler très coûteuse dans une application Web.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Pour compiler le code, copiez-le dans une page code-behind ASP.NET afin qu’il remplace tout le code existant. La page web ASP.NET doit contenir les contrôles suivants :  
  
- Un contrôle <xref:System.Web.UI.WebControls.Label>, qui n’est pas référencé dans le code. Définissez sa propriété <xref:System.Web.UI.WebControls.TextBox.Text%2A> sur « Entrez un nombre : ».  
  
- un contrôle <xref:System.Web.UI.WebControls.TextBox> nommé `NumericString` ;  
  
- un contrôle <xref:System.Web.UI.WebControls.Button> nommé `OKButton` ; Définissez sa propriété <xref:System.Web.UI.WebControls.Button.Text%2A> sur « OK ».  
  
 Remplacez le nom de la classe `NumericUserInput` par le nom de la classe définie par l’attribut `Inherits` de la directive `Page` de la page ASP.NET. Remplacez le nom de la référence d’objet `NumericInput` par le nom défini par l’attribut `id` de la balise `form` de la page ASP.NET.  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Pour empêcher un utilisateur d’injecter un script dans le flux de données HTML, l’entrée de l’utilisateur ne doit jamais être renvoyée directement dans la réponse du serveur. Elle doit être encodée à l’aide de la méthode <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- [Exécution d’opérations de mise en forme](../../../docs/standard/base-types/performing-formatting-operations.md)
- [Analyse de chaînes numériques](../../../docs/standard/base-types/parsing-numeric.md)
