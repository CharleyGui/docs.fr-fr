---
title: 'Procédure : afficher des informations de date et d’heure localisées pour les utilisateurs du web'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- formatting [.NET Framework], dates
- parsing strings [.NET Framework], date and time strings
- localization [.NET Framework], date and time displays
- formatting [.NET Framework], localized data
- displaying date and time data
- localized date displays [.NET Framework]
ms.assetid: 377fe93c-32be-421a-a30a-be639a46ede8
dev_langs:
- csharp
- vb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c50cdf93d8cfcefeffd35290d26dfa432a241e1
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882486"
---
# <a name="how-to-display-localized-date-and-time-information-to-web-users"></a>Procédure : afficher des informations de date et d’heure localisées pour les utilisateurs du web
Une page Web pouvant être affichée n’importe où dans le monde, les opérations qui analysent et mettent en forme les valeurs de date et d’heure ne doivent pas s’appuyer sur un format par défaut (généralement le format de la culture locale du serveur Web) lors de l’interaction avec l’utilisateur. Au lieu de cela, les formulaires Web qui gèrent les chaînes de date et d’heure saisies par l’utilisateur doivent analyser les chaînes en utilisant la culture préférée de l’utilisateur. De même, les données de date et d’heure doivent être affichées à l’utilisateur dans un format conforme à sa culture. Cette rubrique montre comment procéder.  
  
## <a name="to-parse-date-and-time-strings-input-by-the-user"></a>Pour analyser les chaînes de date et d’heure saisies par l’utilisateur  
  
1. Déterminez si le tableau de chaînes retourné par la propriété <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> est rempli. Si ce n’est pas le cas, passez à l’étape 6.  
  
2. Si le tableau de chaînes retourné par la propriété <xref:System.Web.HttpRequest.UserLanguages%2A> est rempli, récupérez son premier élément. Le premier élément indique la langue et la région par défaut ou préférées de l’utilisateur.  
  
3. Instanciez un objet <xref:System.Globalization.CultureInfo> représentant la culture préférée de l’utilisateur en appelant le constructeur <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType>.  
  
4. Appelez la méthode `TryParse` ou `Parse` de type <xref:System.DateTime> ou <xref:System.DateTimeOffset> pour tester la conversion. Utilisez une surcharge de la méthode `TryParse` ou `Parse` avec un paramètre `provider` et transférez-y un des éléments suivants :  
  
    - L’objet <xref:System.Globalization.CultureInfo> créé à l’étape 3  
  
    - L’objet <xref:System.Globalization.DateTimeFormatInfo> retourné par la propriété <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> de l’objet <xref:System.Globalization.CultureInfo> créé à l’étape 3  
  
5. Si la conversion échoue, répétez les étapes 2 à 4 pour chaque élément restant dans le tableau de chaînes retourné par la propriété <xref:System.Web.HttpRequest.UserLanguages%2A>.  
  
6. Si la conversion échoue toujours ou si le tableau de chaînes retourné par la propriété <xref:System.Web.HttpRequest.UserLanguages%2A> est vide, analysez la chaîne à l’aide de la culture invariante retournée par la propriété <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.  
  
## <a name="to-parse-the-local-date-and-time-of-the-users-request"></a>Pour analyser la date et l’heure locales de la demande de l’utilisateur  
  
1. Ajoutez un contrôle <xref:System.Web.UI.WebControls.HiddenField> à votre formulaire Web.  
  
2. Créez une fonction JavaScript qui gère l’événement `onClick` d’un bouton `Submit` en inscrivant la date et l’heure actuelles ainsi que le décalage de fuseau horaire par rapport au temps universel coordonné (UTC) pour la propriété <xref:System.Web.UI.WebControls.HiddenField.Value%2A>. Utilisez un délimiteur (par exemple, un point-virgule) pour séparer les deux composants de la chaîne.  
  
3. Utilisez l’événement <xref:System.Web.UI.Control.PreRender> du formulaire Web pour injecter la fonction dans le flux sortant HTML en transférant le texte du script à la méthode <xref:System.Web.UI.ClientScriptManager.RegisterClientScriptBlock%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Boolean%29?displayProperty=nameWithType>.  
  
4. Connectez le gestionnaire d’événements à l’événement `onClick` du bouton `Submit` en communiquant le nom de la fonction JavaScript à l’attribut `OnClientClick` du bouton `Submit`.  
  
5. Créez un gestionnaire pour l’événement <xref:System.Web.UI.WebControls.Button.Click> du bouton `Submit`.  
  
6. Dans le Gestionnaire d’événements, déterminez si le tableau de chaînes retourné par la propriété <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> est rempli. Si ce n’est pas le cas, passez à l’étape 14.  
  
7. Si le tableau de chaînes retourné par la propriété <xref:System.Web.HttpRequest.UserLanguages%2A> est rempli, récupérez son premier élément. Le premier élément indique la langue et la région par défaut ou préférées de l’utilisateur.  
  
8. Instanciez un objet <xref:System.Globalization.CultureInfo> représentant la culture préférée de l’utilisateur en appelant le constructeur <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType>.  
  
9. Transférez la chaîne affectée à la propriété <xref:System.Web.UI.WebControls.HiddenField.Value%2A> à la méthode <xref:System.String.Split%2A> pour stocker la représentation de la chaîne de l’heure et de la date locales de l’utilisateur ainsi que la représentation de la chaîne du décalage de fuseau horaire de l’utilisateur dans des éléments de tableau distincts.  
  
10. Appelez la méthode <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> ou <xref:System.DateTime.TryParse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%2CSystem.DateTime%40%29?displayProperty=nameWithType> pour convertir la date et l’heure de la demande de l’utilisateur en une valeur <xref:System.DateTime>. Utilisez une surcharge de la méthode `provider` avec un paramètre et transférez-y un des éléments suivants :  
  
    - L’objet <xref:System.Globalization.CultureInfo> créé à l’étape 8.  
  
    - L’objet <xref:System.Globalization.DateTimeFormatInfo> retourné par la propriété <xref:System.Globalization.CultureInfo.DateTimeFormat%2A> de l’objet <xref:System.Globalization.CultureInfo> créé à l’étape 8.  
  
11. Si l’opération d’analyse à l’étape 10 échoue, passez à l’étape 13. Sinon, appelez la méthode <xref:System.UInt32.Parse%28System.String%29?displayProperty=nameWithType> pour convertir la représentation de la chaîne du décalage de fuseau horaire de l’utilisateur en un entier.  
  
12. Instanciez un objet <xref:System.DateTimeOffset> représentant l’heure locale de l’utilisateur en appelant le constructeur <xref:System.DateTimeOffset.%23ctor%28System.DateTime%2CSystem.TimeSpan%29?displayProperty=nameWithType>.  
  
13. Si la conversion de l’étape 10 échoue, répétez les étapes 7 à 12 pour chaque élément restant dans le tableau de chaînes retourné par la propriété <xref:System.Web.HttpRequest.UserLanguages%2A>.  
  
14. Si la conversion échoue toujours ou si le tableau de chaînes retourné par la propriété <xref:System.Web.HttpRequest.UserLanguages%2A> est vide, analysez la chaîne à l’aide de la culture invariante retournée par la propriété <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Puis répétez les étapes 7 à 12.  
  
 Vous obtenez un objet <xref:System.DateTimeOffset> qui représente l’heure locale de l’utilisateur de votre page Web. Vous pouvez ensuite déterminer l’heure UTC équivalente en appelant la méthode <xref:System.DateTimeOffset.ToUniversalTime%2A>. Vous pouvez également déterminer la date et l’heure équivalentes sur votre serveur Web en appelant la méthode <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> puis en transférant la valeur <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> comme fuseau horaire dans lequel l’heure doit être convertie.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant contient la source HTML et le code d’un formulaire Web ASP.NET qui invite l’utilisateur à entrer une valeur de date et d’heure. Un script côté client inscrit également dans un champ masqué des informations sur la date et l’heure locales de la demande de l’utilisateur ainsi que décalage du fuseau horaire de l’utilisateur par rapport à l’heure UTC. Ces informations sont ensuite analysées par le serveur, qui retourne une page Web affichant l’entrée de l’utilisateur. Il affiche également la date et l’heure de la demande de l’utilisateur en utilisant l’heure locale de l’utilisateur, l’heure sur le serveur et l’heure UTC.  
  
 [!code-aspx-csharp[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/cs/GetDateInfo.aspx#1)]
 [!code-aspx-vb[Formatting.HowTo.ParseDateInput#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.ParseDateInput/vb/GetDateInfo.aspx#1)]
  
 Le script côté client appelle la méthode JavaScript `toLocaleString`. Il génère une chaîne qui suit les conventions de mise en forme des paramètres régionaux de l’utilisateur, les plus susceptibles d’être correctement analysés sur le serveur.  
  
 La propriété <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> est remplie par les noms de la culture qui figurent dans les en-têtes `Accept-Language` inclus dans une requête HTTP. Toutefois, certains navigateurs n’incluent pas les en-têtes `Accept-Language` dans leurs demandes, et les utilisateurs peuvent également supprimer totalement ces en-têtes. Il est donc important de disposer d’une culture de secours lorsque vous analysez l’entrée de l’utilisateur. En général, la culture de secours est la culture invariante retournée par <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Les utilisateurs peuvent également fournir à Internet Explorer des noms de cultures qu’ils entrent dans une zone de texte, avec la possibilité que ces noms de cultures ne sont pas valides. Il est donc important d’utiliser la gestion des exceptions quand vous instanciez un objet <xref:System.Globalization.CultureInfo>.  
  
 Quand il est extrait d’une requête HTTP soumise par Internet Explorer, le tableau <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType> est rempli selon l’ordre de préférence de l’utilisateur. Le premier élément du tableau contient le nom de la culture/région principale de l’utilisateur. Si le tableau contient d’autres éléments, Internet Explorer leur assigne arbitrairement un spécificateur de qualité, séparé du nom de culture par un point virgule. Par exemple, une entrée pour la culture fr-FR peut prendre la forme `fr-FR;q=0.7`.  
  
 L’exemple appelle le constructeur <xref:System.Globalization.CultureInfo.%23ctor%2A> avec son paramètre `useUserOverride` défini sur `false` pour créer un nouvel objet <xref:System.Globalization.CultureInfo>. Cela garantit que, si le nom de la culture est le nom de la culture par défaut sur le serveur, le nouvel objet <xref:System.Globalization.CultureInfo> créé par le constructeur de classe contient les paramètres par défaut d’une culture et ne reflète pas les paramètres substitués en utilisant l’application **Options régionales et linguistiques du serveur**. Les valeurs des paramètres substitués sur le serveur sont peu susceptibles d’exister sur le système de l’utilisateur ou d’apparaître dans l’entrée de l’utilisateur.  
  
 Comme cet exemple analyse deux représentations d’une chaîne de date et d’heure (une entrée par l’utilisateur, et l’autre stockée dans le champ masqué), il définit les objets <xref:System.Globalization.CultureInfo> qui peuvent être nécessaires par avance. Il crée un tableau d’objets <xref:System.Globalization.CultureInfo> supérieur d’une unité au nombre d’éléments retournés par la propriété <xref:System.Web.HttpRequest.UserLanguages%2A?displayProperty=nameWithType>. Il instancie ensuite un objet <xref:System.Globalization.CultureInfo> pour chaque chaîne de langue/région, ainsi qu’un objet <xref:System.Globalization.CultureInfo> représentant <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.  
  
 Votre code peut appeler la méthode <xref:System.DateTime.Parse%2A> ou <xref:System.DateTime.TryParse%2A> pour convertir la représentation de chaîne de date et d’heure de l’utilisateur en une valeur <xref:System.DateTime>. Des appels répétés à une méthode d’analyse peuvent être nécessaires pour une opération d’analyse unique. Par conséquent, la méthode <xref:System.DateTime.TryParse%2A> est préférable car elle retourne `false` si une opération d’analyse échoue. En revanche, la gestion d’exceptions répétées générées par la méthode <xref:System.DateTime.Parse%2A> peut se révéler très coûteuse dans une application Web.  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Pour compiler le code, créez une page web ASP.NET sans code-behind. Copiez ensuite l’exemple dans la page Web pour qu’il remplace tout le code existant. La page web ASP.NET doit contenir les contrôles suivants :  
  
- Un contrôle <xref:System.Web.UI.WebControls.Label>, qui n’est pas référencé dans le code. Définissez sa propriété <xref:System.Web.UI.WebControls.TextBox.Text%2A> sur « Entrez un nombre : ».  
  
- un contrôle <xref:System.Web.UI.WebControls.TextBox> nommé `DateString` ;  
  
- un contrôle <xref:System.Web.UI.WebControls.Button> nommé `OKButton` ; Définissez sa propriété <xref:System.Web.UI.WebControls.Button.Text%2A> sur « OK ».  
  
- un contrôle <xref:System.Web.UI.WebControls.HiddenField> nommé `DateInfo` ;  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Pour empêcher un utilisateur d’injecter un script dans le flux de données HTML, l’entrée de l’utilisateur ne doit jamais être renvoyée directement dans la réponse du serveur. Elle doit être encodée à l’aide de la méthode <xref:System.Web.HttpServerUtility.HtmlEncode%2A?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Voir aussi

- [Exécution d’opérations de mise en forme](../../../docs/standard/base-types/performing-formatting-operations.md)
- [Standard Date and Time Format Strings](../../../docs/standard/base-types/standard-date-and-time-format-strings.md)
- [Custom Date and Time Format Strings](../../../docs/standard/base-types/custom-date-and-time-format-strings.md)
- [Analyse de chaînes de date et d’heure](../../../docs/standard/base-types/parsing-datetime.md)
