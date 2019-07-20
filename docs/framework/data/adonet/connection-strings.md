---
title: Chaînes de connexion dans ADO.NET
ms.date: 10/10/2018
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: 02fe8d984f1287673477bb142b3f9626e248898e
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363751"
---
# <a name="connection-strings-in-adonet"></a><span data-ttu-id="b7181-102">Chaînes de connexion dans ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b7181-102">Connection Strings in ADO.NET</span></span>

<span data-ttu-id="b7181-103">Une chaîne de connexion contient des informations d'initialisation qui sont passées en tant que paramètre d'un fournisseur de données à une source de données.</span><span class="sxs-lookup"><span data-stu-id="b7181-103">A connection string contains initialization information that is passed as a parameter from a data provider to a data source.</span></span> <span data-ttu-id="b7181-104">Le fournisseur de données reçoit la chaîne de connexion en tant que <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="b7181-104">The data provider receives the connection string as the value of the <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="b7181-105">Le fournisseur analyse la chaîne de connexion et s’assure que la syntaxe est correcte et que les mots clés sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="b7181-105">The provider parses the connection string and ensures that the syntax is correct and that the keywords are supported.</span></span> <span data-ttu-id="b7181-106">La <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> méthode transmet ensuite les paramètres de connexion analysés à la source de données.</span><span class="sxs-lookup"><span data-stu-id="b7181-106">Then the <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> method passes the parsed connection parameters to the data source.</span></span> <span data-ttu-id="b7181-107">La source de données effectue une validation supplémentaire et établit une connexion.</span><span class="sxs-lookup"><span data-stu-id="b7181-107">The data source performs further validation and establishes a connection.</span></span>

## <a name="connection-string-syntax"></a><span data-ttu-id="b7181-108">Syntaxe de chaîne de connexion</span><span class="sxs-lookup"><span data-stu-id="b7181-108">Connection string syntax</span></span>

<span data-ttu-id="b7181-109">Une chaîne de connexion est une liste délimitée par des points-virgules de paires de paramètres clé/valeur:</span><span class="sxs-lookup"><span data-stu-id="b7181-109">A connection string is a semicolon-delimited list of key/value parameter pairs:</span></span>

```
keyword1=value; keyword2=value;
```

<span data-ttu-id="b7181-110">Les mots clés ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="b7181-110">Keywords are not case-sensitive.</span></span> <span data-ttu-id="b7181-111">Toutefois, les valeurs peuvent respecter la casse, en fonction de la source de données.</span><span class="sxs-lookup"><span data-stu-id="b7181-111">Values, however, may be case-sensitive, depending on the data source.</span></span> <span data-ttu-id="b7181-112">Les mots clés et les valeurs peuvent contenir des [espaces blancs](https://en.wikipedia.org/wiki/Whitespace_character#Unicode).</span><span class="sxs-lookup"><span data-stu-id="b7181-112">Both keywords and values may contain [whitespace characters](https://en.wikipedia.org/wiki/Whitespace_character#Unicode).</span></span> <span data-ttu-id="b7181-113">Les espaces blancs de début et de fin sont ignorés dans les mots clés et les valeurs sans guillemets.</span><span class="sxs-lookup"><span data-stu-id="b7181-113">Leading and trailing white space is ignored in keywords and unquoted values.</span></span>

<span data-ttu-id="b7181-114">Si une valeur contient le point-virgule, les [caractères de contrôle Unicode](https://en.wikipedia.org/wiki/Unicode_control_characters)ou les espaces blancs de début ou de fin, elle doit être placée entre guillemets simples ou doubles.</span><span class="sxs-lookup"><span data-stu-id="b7181-114">If a value contains the semicolon, [Unicode control characters](https://en.wikipedia.org/wiki/Unicode_control_characters), or leading or trailing white space, it must be enclosed in single or double quotation marks.</span></span> <span data-ttu-id="b7181-115">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b7181-115">For example:</span></span>

```
Keyword=" whitespace  ";
Keyword='special;character';
```

<span data-ttu-id="b7181-116">Le caractère englobant peut ne pas se trouver dans la valeur qu’il englobe.</span><span class="sxs-lookup"><span data-stu-id="b7181-116">The enclosing character may not occur within the value it encloses.</span></span> <span data-ttu-id="b7181-117">Par conséquent, une valeur contenant des guillemets simples peut être placée entre guillemets doubles, et vice versa:</span><span class="sxs-lookup"><span data-stu-id="b7181-117">Therefore, a value containing single quotation marks can be enclosed only in double quotation marks, and vice versa:</span></span>

```
Keyword='double"quotation;mark';
Keyword="single'quotation;mark";
```

<span data-ttu-id="b7181-118">Vous pouvez également échapper le caractère englobant à l’aide de deux d’entre eux:</span><span class="sxs-lookup"><span data-stu-id="b7181-118">You can also escape the enclosing character by using two of them together:</span></span>

```
Keyword="double""quotation";
Keyword='single''quotation';
```

<span data-ttu-id="b7181-119">Les guillemets eux-mêmes, ainsi que le signe égal, ne nécessitent pas d’échappement, donc les chaînes de connexion suivantes sont valides:</span><span class="sxs-lookup"><span data-stu-id="b7181-119">The quotation marks themselves, as well as the equals sign, do not require escaping, so the following connection strings are valid:</span></span>

```
Keyword=no "escaping" 'required';
Keyword=a=b=c
```

<span data-ttu-id="b7181-120">Étant donné que chaque valeur est lue jusqu’au point-virgule suivant ou jusqu’à la fin de la chaîne, `a=b=c`la valeur dans le dernier exemple est, et le point-virgule final est facultatif.</span><span class="sxs-lookup"><span data-stu-id="b7181-120">Since each value is read till the next semicolon or the end of string, the value in the latter example is `a=b=c`, and the final semicolon is optional.</span></span>

<span data-ttu-id="b7181-121">Toutes les chaînes de connexion partagent la même syntaxe de base décrite ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="b7181-121">All connection strings share the same basic syntax described above.</span></span> <span data-ttu-id="b7181-122">Toutefois, l’ensemble des mots clés reconnus dépend du fournisseur et a évolué au fil des années à partir des API antérieures telles que *ODBC*.</span><span class="sxs-lookup"><span data-stu-id="b7181-122">The set of recognized keywords depends on the provider, however, and has evolved over the years from earlier APIs such as *ODBC*.</span></span> <span data-ttu-id="b7181-123">Le fournisseur de données *.NET Framework* pour *SQL Server* (`SqlClient`) prend en charge de nombreux mots clés d’anciennes API, mais il est généralement plus flexible et accepte des synonymes pour un grand nombre des mots clés de chaîne de connexion courants.</span><span class="sxs-lookup"><span data-stu-id="b7181-123">The *.NET Framework* data provider for *SQL Server* (`SqlClient`) supports many keywords from older APIs, but is generally more flexible and accepts synonyms for many of the common connection string keywords.</span></span>

<span data-ttu-id="b7181-124">Les erreurs de frappe peuvent entraîner des erreurs.</span><span class="sxs-lookup"><span data-stu-id="b7181-124">Typing mistakes can cause errors.</span></span> <span data-ttu-id="b7181-125">Par exemple, `Integrated Security=true` est valide, mais `IntegratedSecurity=true` génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="b7181-125">For example, `Integrated Security=true` is valid, but `IntegratedSecurity=true` causes an error.</span></span>

<span data-ttu-id="b7181-126">Les chaînes de connexion construites manuellement au moment de l’exécution à partir d’une entrée utilisateur non validée sont vulnérables aux attaques par injection de chaîne et mettent en péril la sécurité au niveau de la source de données.</span><span class="sxs-lookup"><span data-stu-id="b7181-126">Connection strings constructed manually at run time from unvalidated user input are vulnerable to string-injection attacks and jeopardize security at the data source.</span></span> <span data-ttu-id="b7181-127">Pour résoudre ces problèmes, *ADO.NET* 2,0 a introduit les générateurs de [chaînes de connexion](../../../../docs/framework/data/adonet/connection-string-builders.md) pour chaque fournisseur de données *.NET Framework* .</span><span class="sxs-lookup"><span data-stu-id="b7181-127">To address these problems, *ADO.NET* 2.0 introduced [connection string builders](../../../../docs/framework/data/adonet/connection-string-builders.md) for each *.NET Framework* data provider.</span></span> <span data-ttu-id="b7181-128">Ces générateurs de chaînes de connexion exposent des paramètres en tant que propriétés fortement typées et permettent de valider la chaîne de connexion avant qu’elle ne soit envoyée à la source de données.</span><span class="sxs-lookup"><span data-stu-id="b7181-128">These connection string builders expose parameters as strongly-typed properties, and make it possible to validate the connection string before it's sent to the data source.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="b7181-129">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b7181-129">In This Section</span></span>

<span data-ttu-id="b7181-130">[Générateurs de chaînes de connexion](../../../../docs/framework/data/adonet/connection-string-builders.md)</span><span class="sxs-lookup"><span data-stu-id="b7181-130">[Connection String Builders](../../../../docs/framework/data/adonet/connection-string-builders.md)</span></span>\
<span data-ttu-id="b7181-131">Montre comment utiliser les classes `ConnectionStringBuilder` pour générer des chaînes de connexion valides au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="b7181-131">Demonstrates how to use the `ConnectionStringBuilder` classes to construct valid connection strings at run time.</span></span>

<span data-ttu-id="b7181-132">[Chaînes de connexion et fichiers de configuration](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)</span><span class="sxs-lookup"><span data-stu-id="b7181-132">[Connection Strings and Configuration Files](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)</span></span>\
<span data-ttu-id="b7181-133">Montre comment stocker et extraire des chaînes de connexion dans des fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="b7181-133">Demonstrates how to store and retrieve connection strings in configuration files.</span></span>

<span data-ttu-id="b7181-134">[Syntaxe de chaîne de connexion](../../../../docs/framework/data/adonet/connection-string-syntax.md)</span><span class="sxs-lookup"><span data-stu-id="b7181-134">[Connection String Syntax](../../../../docs/framework/data/adonet/connection-string-syntax.md)</span></span>\
<span data-ttu-id="b7181-135">Décrit comment configurer des chaînes de connexion spécifiques au fournisseur pour `SqlClient`, `OracleClient`, `OleDb` et `Odbc`.</span><span class="sxs-lookup"><span data-stu-id="b7181-135">Describes how to configure provider-specific connection strings for `SqlClient`, `OracleClient`, `OleDb`, and `Odbc`.</span></span>

<span data-ttu-id="b7181-136">[Protection des informations de connexion](../../../../docs/framework/data/adonet/protecting-connection-information.md)</span><span class="sxs-lookup"><span data-stu-id="b7181-136">[Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md)</span></span>\
<span data-ttu-id="b7181-137">Montre des techniques pour la protection des informations utilisées pour la connexion à une source de données.</span><span class="sxs-lookup"><span data-stu-id="b7181-137">Demonstrates techniques for protecting information used to connect to a data source.</span></span>

## <a name="see-also"></a><span data-ttu-id="b7181-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7181-138">See also</span></span>

- [<span data-ttu-id="b7181-139">Connexion à une source de données</span><span class="sxs-lookup"><span data-stu-id="b7181-139">Connecting to a Data Source</span></span>](/cpp/data/odbc/connecting-to-a-data-source)
- [<span data-ttu-id="b7181-140">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="b7181-140">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
