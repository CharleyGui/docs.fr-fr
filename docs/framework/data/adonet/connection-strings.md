---
title: Chaînes de connexion dans ADO.NET
ms.date: 10/10/2018
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: 3b7cb0ab061da8364a9fecc3868ba9aaf7501577
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881160"
---
# <a name="connection-strings-in-adonet"></a><span data-ttu-id="37344-102">Chaînes de connexion dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="37344-102">Connection Strings in ADO.NET</span></span>

<span data-ttu-id="37344-103">Une chaîne de connexion contient des informations d'initialisation qui sont passées en tant que paramètre d'un fournisseur de données à une source de données.</span><span class="sxs-lookup"><span data-stu-id="37344-103">A connection string contains initialization information that is passed as a parameter from a data provider to a data source.</span></span> <span data-ttu-id="37344-104">Le fournisseur de données reçoit la chaîne de connexion en tant que la valeur de la <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> propriété.</span><span class="sxs-lookup"><span data-stu-id="37344-104">The data provider receives the connection string as the value of the <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="37344-105">Le fournisseur analyse la chaîne de connexion et vérifie que la syntaxe est correcte et que les mots clés sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="37344-105">The provider parses the connection string and ensures that the syntax is correct and that the keywords are supported.</span></span> <span data-ttu-id="37344-106">Le <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> méthode passe les paramètres de connexion analysée à la source de données.</span><span class="sxs-lookup"><span data-stu-id="37344-106">Then the <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> method passes the parsed connection parameters to the data source.</span></span> <span data-ttu-id="37344-107">La source de données effectue une validation supplémentaire et établit une connexion.</span><span class="sxs-lookup"><span data-stu-id="37344-107">The data source performs further validation and establishes a connection.</span></span>

## <a name="connection-string-syntax"></a><span data-ttu-id="37344-108">Syntaxe de chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="37344-108">Connection string syntax</span></span>

<span data-ttu-id="37344-109">Une chaîne de connexion est une liste délimitée par des points-virgules de paires clé/valeur de paramètre :</span><span class="sxs-lookup"><span data-stu-id="37344-109">A connection string is a semicolon-delimited list of key/value parameter pairs:</span></span>

```
keyword1=value; keyword2=value;
```

<span data-ttu-id="37344-110">Mots clés ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="37344-110">Keywords are not case-sensitive.</span></span> <span data-ttu-id="37344-111">Valeurs, toutefois, peuvent être la casse, en fonction de la source de données.</span><span class="sxs-lookup"><span data-stu-id="37344-111">Values, however, may be case-sensitive, depending on the data source.</span></span> <span data-ttu-id="37344-112">Peuvent contenir des mots clés et valeurs [blancs](https://en.wikipedia.org/wiki/Whitespace_character#Unicode).</span><span class="sxs-lookup"><span data-stu-id="37344-112">Both keywords and values may contain [whitespace characters](https://en.wikipedia.org/wiki/Whitespace_character#Unicode).</span></span> <span data-ttu-id="37344-113">Espaces de début et de fin est ignoré dans les mots clés et guillemets valeurs.</span><span class="sxs-lookup"><span data-stu-id="37344-113">Leading and trailing white space is ignored in keywords and unquoted values.</span></span>

<span data-ttu-id="37344-114">Si une valeur contient le point-virgule, [caractères de contrôle Unicode](https://en.wikipedia.org/wiki/Unicode_control_characters), ou à gauche ou un espace blanc, elle doit figurer entre guillemets simples ou doubles.</span><span class="sxs-lookup"><span data-stu-id="37344-114">If a value contains the semicolon, [Unicode control characters](https://en.wikipedia.org/wiki/Unicode_control_characters), or leading or trailing white space, it must be enclosed in single or double quotation marks.</span></span> <span data-ttu-id="37344-115">Exemple :</span><span class="sxs-lookup"><span data-stu-id="37344-115">For example:</span></span>

```
Keyword=" whitespace  ";
Keyword='special;character';
```

<span data-ttu-id="37344-116">Le caractère englobant n’a pas peut se produire au sein de la valeur qu’elle comprend.</span><span class="sxs-lookup"><span data-stu-id="37344-116">The enclosing character may not occur within the value it encloses.</span></span> <span data-ttu-id="37344-117">Par conséquent, une valeur contenant des guillemets simples peut être placées entre uniquement dans des guillemets doubles et vice versa :</span><span class="sxs-lookup"><span data-stu-id="37344-117">Therefore, a value containing single quotation marks can be enclosed only in double quotation marks, and vice versa:</span></span>

```
Keyword='double"quotation;mark';
Keyword="single'quotation;mark";
```

<span data-ttu-id="37344-118">Les guillemets eux-mêmes, ainsi que le signe égal, ne nécessite pas d’échappement, par conséquent, les chaînes de connexion suivantes sont valides :</span><span class="sxs-lookup"><span data-stu-id="37344-118">The quotation marks themselves, as well as the equals sign, do not require escaping, so the following connection strings are valid:</span></span>

```
Keyword=no "escaping" 'required';
Keyword=a=b=c
```

<span data-ttu-id="37344-119">Dans la mesure où chaque valeur est lue jusqu'à ce que le point-virgule suivant ou à la fin de chaîne, la valeur dans l’exemple de ce dernier est `a=b=c`, et le point-virgule final est facultatif.</span><span class="sxs-lookup"><span data-stu-id="37344-119">Since each value is read till the next semicolon or the end of string, the value in the latter example is `a=b=c`, and the final semicolon is optional.</span></span>

<span data-ttu-id="37344-120">Toutes les chaînes de connexion partagent la même syntaxe de base décrite ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="37344-120">All connection strings share the same basic syntax described above.</span></span> <span data-ttu-id="37344-121">L’ensemble des mots clés reconnus varie selon le fournisseur, toutefois et a évolué au fil des années à partir d’API antérieures telles que *ODBC*.</span><span class="sxs-lookup"><span data-stu-id="37344-121">The set of recognized keywords depends on the provider, however, and has evolved over the years from earlier APIs such as *ODBC*.</span></span> <span data-ttu-id="37344-122">Le *.NET Framework* fournisseur de données pour *SQL Server* (`SqlClient`) prend en charge de nombreux mots clés à partir d’une API plus anciennes, mais se montre généralement plus souple et accepte des synonymes pour la plupart de la chaîne de connexion courantes mots clés.</span><span class="sxs-lookup"><span data-stu-id="37344-122">The *.NET Framework* data provider for *SQL Server* (`SqlClient`) supports many keywords from older APIs, but is generally more flexible and accepts synonyms for many of the common connection string keywords.</span></span>

<span data-ttu-id="37344-123">Fautes de frappe peut provoquer des erreurs.</span><span class="sxs-lookup"><span data-stu-id="37344-123">Typing mistakes can cause errors.</span></span> <span data-ttu-id="37344-124">Par exemple, `Integrated Security=true` est valide, mais `IntegratedSecurity=true` provoque une erreur.</span><span class="sxs-lookup"><span data-stu-id="37344-124">For example, `Integrated Security=true` is valid, but `IntegratedSecurity=true` causes an error.</span></span>

<span data-ttu-id="37344-125">Chaînes de connexion générées manuellement en cours d’exécution à partir de l’entrée utilisateur non validée sont vulnérables aux attaques par injection de chaîne et mettre en péril la sécurité au niveau de la source de données.</span><span class="sxs-lookup"><span data-stu-id="37344-125">Connection strings constructed manually at run time from unvalidated user input are vulnerable to string-injection attacks and jeopardize security at the data source.</span></span> <span data-ttu-id="37344-126">Pour résoudre ces problèmes, *ADO.NET* 2.0 a introduit [générateurs de chaînes de connexion](../../../../docs/framework/data/adonet/connection-string-builders.md) pour chaque *.NET Framework* fournisseur de données.</span><span class="sxs-lookup"><span data-stu-id="37344-126">To address these problems, *ADO.NET* 2.0 introduced [connection string builders](../../../../docs/framework/data/adonet/connection-string-builders.md) for each *.NET Framework* data provider.</span></span> <span data-ttu-id="37344-127">Ces générateurs de chaînes de connexion exposent des paramètres en tant que propriétés fortement typées et le rendent possible de valider la chaîne de connexion avant d’être envoyée à la source de données.</span><span class="sxs-lookup"><span data-stu-id="37344-127">These connection string builders expose parameters as strongly-typed properties, and make it possible to validate the connection string before it's sent to the data source.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="37344-128">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="37344-128">In This Section</span></span>

<span data-ttu-id="37344-129">[Générateurs de chaînes de connexion](../../../../docs/framework/data/adonet/connection-string-builders.md)\\</span><span class="sxs-lookup"><span data-stu-id="37344-129">[Connection String Builders](../../../../docs/framework/data/adonet/connection-string-builders.md)\\</span></span>
<span data-ttu-id="37344-130">Montre comment utiliser les classes `ConnectionStringBuilder` pour générer des chaînes de connexion valides au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="37344-130">Demonstrates how to use the `ConnectionStringBuilder` classes to construct valid connection strings at run time.</span></span>

<span data-ttu-id="37344-131">[Chaînes de connexion et les fichiers de Configuration](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)\\</span><span class="sxs-lookup"><span data-stu-id="37344-131">[Connection Strings and Configuration Files](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)\\</span></span>
<span data-ttu-id="37344-132">Montre comment stocker et extraire des chaînes de connexion dans des fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="37344-132">Demonstrates how to store and retrieve connection strings in configuration files.</span></span>

<span data-ttu-id="37344-133">[Syntaxe de chaîne de connexion](../../../../docs/framework/data/adonet/connection-string-syntax.md)\\</span><span class="sxs-lookup"><span data-stu-id="37344-133">[Connection String Syntax](../../../../docs/framework/data/adonet/connection-string-syntax.md)\\</span></span>
<span data-ttu-id="37344-134">Décrit comment configurer des chaînes de connexion spécifiques au fournisseur pour `SqlClient`, `OracleClient`, `OleDb` et `Odbc`.</span><span class="sxs-lookup"><span data-stu-id="37344-134">Describes how to configure provider-specific connection strings for `SqlClient`, `OracleClient`, `OleDb`, and `Odbc`.</span></span>

<span data-ttu-id="37344-135">[Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md)\\</span><span class="sxs-lookup"><span data-stu-id="37344-135">[Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md)\\</span></span>
<span data-ttu-id="37344-136">Montre des techniques pour la protection des informations utilisées pour la connexion à une source de données.</span><span class="sxs-lookup"><span data-stu-id="37344-136">Demonstrates techniques for protecting information used to connect to a data source.</span></span>

## <a name="see-also"></a><span data-ttu-id="37344-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37344-137">See also</span></span>

- [<span data-ttu-id="37344-138">Connexion à une source de données</span><span class="sxs-lookup"><span data-stu-id="37344-138">Connecting to a Data Source</span></span>](/cpp/data/odbc/connecting-to-a-data-source)
- [<span data-ttu-id="37344-139">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="37344-139">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
