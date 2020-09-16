---
title: Sérialisation binaire
description: Cet article décrit la sérialisation binaire et les types pour lesquels .NET Core le prend en charge. Tenez compte des dangers de la sérialisation binaire et des alternatives à celle-ci.
ms.date: 01/02/2018
helpviewer_keywords:
- binary serialization
- serialization, about serialization
- deserialization
- binary serialization, about serialization
- binary serialization, .net core serialization
- serialization, cross-framework
ms.assetid: 2b1ea3be-1152-4032-b2b3-07794054c405
author: ViktorHofer
ms.openlocfilehash: 2ede74dd8a48735a7ded450d1da6d9cda8fc5ae6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554493"
---
# <a name="binary-serialization"></a>Sérialisation binaire

La sérialisation peut être définie comme le processus de stockage de l'état d'un objet sur un support de stockage. Pendant ce processus, les champs publics et privés de l'objet et le nom de la classe, y compris l'assembly contenant la classe, sont convertis en un flux de données d'octets, écrit ensuite dans un flux de données. Lorsque l'objet est désérialisé par la suite, un clone exact de l'objet d'origine est créé.

Lorsque vous implémentez un mécanisme de sérialisation dans un environnement orienté objet, vous devez faire plusieurs compromis entre facilité d'utilisation et souplesse. Le processus peut être automatisé en grande partie, à condition que vous puissiez suffisamment le contrôler. Par exemple, dans certaines situations, la sérialisation binaire simple n'est pas suffisante ou une raison particulière peut exiger la définition des champs à sérialiser. Les sections suivantes étudient le mécanisme de sérialisation fiable fourni avec .NET et mettent en évidence plusieurs fonctionnalités importantes qui vous permettent de personnaliser le processus en fonction de vos besoins.

> [!NOTE]
> L'état d'un objet encodé UTF-8 ou UTF-7 n'est pas préservé si l'objet est sérialisé et désérialisé à l'aide de différentes versions du .NET Framework.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

La sérialisation binaire permet de modifier les membres privés à l’intérieur d’un objet et par conséquent de modifier l’état de celui-ci. Pour cette raison, d’autres infrastructures de sérialisation, comme <xref:System.Text.Json?displayProperty=fullName> , qui opèrent sur la surface de l’API publique sont recommandées.

## <a name="net-core"></a>.NET Core

.NET Core prend en charge la sérialisation binaire pour un sous-ensemble de types. Vous pouvez voir la liste des types pris en charge dans la section [types sérialisables](#serializable-types) qui suit. Les types répertoriés sont garantis comme étant sérialisables entre .NET Framework 4.5.1 et les versions ultérieures et entre .NET Core 2,0 et versions ultérieures. D’autres implémentations de .NET, telles que mono, ne sont pas officiellement prises en charge, mais doivent également fonctionner.

### <a name="serializable-types"></a>Types sérialisables

> [!div class="mx-tdCol2BreakAll"]
> | Type | Notes |
> | - | - |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderInternalCompilerException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.AccessViolationException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.AggregateException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.ApplicationException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.ArgumentException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.ArgumentNullException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.ArgumentOutOfRangeException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.ArithmeticException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Array?displayProperty=nameWithType> | |
> | <xref:System.ArraySegment%601?displayProperty=nameWithType> | |
> | <xref:System.ArrayTypeMismatchException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Attribute?displayProperty=nameWithType> | |
> | <xref:System.BadImageFormatException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Boolean?displayProperty=nameWithType> | |
> | <xref:System.Byte?displayProperty=nameWithType> | |
> | <xref:System.CannotUnloadAppDomainException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Char?displayProperty=nameWithType> | |
> | <xref:System.Collections.ArrayList?displayProperty=nameWithType> | |
> | <xref:System.Collections.BitArray?displayProperty=nameWithType> | |
> | <xref:System.Collections.Comparer?displayProperty=nameWithType> | |
> | <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Collections.Generic.KeyValuePair%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.LinkedList%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedSet%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Hashtable?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.Collection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Queue?displayProperty=nameWithType> | |
> | <xref:System.Collections.SortedList?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.HybridDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.ListDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.StringCollection?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.StringDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Stack?displayProperty=nameWithType> | |
> | `System.Collections.Generic.NonRandomizedStringEqualityComparer` | À partir de .NET Core 2.0.4. |
> | <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType> | |
> | <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.ComponentModel.Design.CheckoutException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.ComponentModel.InvalidAsynchronousStateException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.ComponentModel.LicenseException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4.<br/>La sérialisation de .NET Framework à .NET Core n’est pas prise en charge. |
> | <xref:System.ComponentModel.WarningException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.ComponentModel.Win32Exception?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Configuration.ConfigurationException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Configuration.Provider.ProviderException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Configuration.SettingsPropertyIsReadOnlyException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Configuration.SettingsPropertyNotFoundException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Configuration.SettingsPropertyWrongTypeException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.ContextMarshalException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.DBNull?displayProperty=nameWithType> | À compter de .NET Core 2.0.2 et versions ultérieures. |
> | <xref:System.Data.Common.DbException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Data.ConstraintException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Data.DBConcurrencyException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Data.DataException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Data.DataSet?displayProperty=nameWithType> | |
> | <xref:System.Data.DataTable?displayProperty=nameWithType> | Si vous définissez `RemotingFormat` sur `SerializationFormat.Binary` , il ne peut être échangé qu’avec .net Core 2,1 et versions ultérieures. |
> | <xref:System.Data.DeletedRowInaccessibleException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Data.DuplicateNameException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Data.EvaluateException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Data.InRowChangingEventException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Data.InvalidConstraintException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Data.InvalidExpressionException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Data.MissingPrimaryKeyException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Data.NoNullAllowedException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Data.Odbc.OdbcException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Data.OperationAbortedException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Data.PropertyCollection?displayProperty=nameWithType> | |
> | <xref:System.Data.ReadOnlyException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Data.RowNotInTableException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Data.SqlClient.SqlException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4.<br/>La sérialisation de .NET Framework à .NET Core n’est pas prise en charge |
> | <xref:System.Data.SqlTypes.SqlAlreadyFilledException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlNotFilledException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Data.SqlTypes.SqlNullValueException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlTruncateException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Data.SqlTypes.SqlTypeException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Data.StrongTypingException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Data.SyntaxErrorException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Data.VersionNotFoundException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.DataMisalignedException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.DateTime?displayProperty=nameWithType> | |
> | <xref:System.DateTimeOffset?displayProperty=nameWithType> | |
> | <xref:System.Decimal?displayProperty=nameWithType> | |
> | `System.Diagnostics.Contracts.ContractException` | À partir de .NET Core 2.0.4. |
> | <xref:System.Diagnostics.Tracing.EventSourceException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.AccountManagement.MultipleMatchesException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.AccountManagement.NoMatchingPrincipalException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.AccountManagement.PasswordException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalExistsException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalOperationException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalServerDownException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectExistsException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectNotFoundException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryOperationException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryServerDownException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.ActiveDirectory.ForestTrustCollisionException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.ActiveDirectory.SyncFromAllServersOperationException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.DirectoryServicesCOMException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.Protocols.BerConversionException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.Protocols.DirectoryException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.Protocols.DirectoryOperationException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.Protocols.LdapException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.Protocols.TlsOperationException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.DivideByZeroException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.DllNotFoundException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Double?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Color?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Point?displayProperty=nameWithType> | |
> | <xref:System.Drawing.PointF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Rectangle?displayProperty=nameWithType> | |
> | <xref:System.Drawing.RectangleF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Size?displayProperty=nameWithType> | |
> | <xref:System.Drawing.SizeF?displayProperty=nameWithType> | |
> | <xref:System.DuplicateWaitObjectException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.EntryPointNotFoundException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Enum?displayProperty=nameWithType> | |
> | <xref:System.EventArgs?displayProperty=nameWithType> | À partir de .NET Core 2.0.6. |
> | <xref:System.Exception?displayProperty=nameWithType> | |
> | <xref:System.ExecutionEngineException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.FieldAccessException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.FormatException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> | |
> | <xref:System.Globalization.CultureNotFoundException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Globalization.SortVersion?displayProperty=nameWithType> | |
> | <xref:System.Guid?displayProperty=nameWithType> | |
> | `System.IO.Compression.ZLibException` | À partir de .NET Core 2.0.4. |
> | <xref:System.IO.DriveNotFoundException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.IO.EndOfStreamException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.IO.FileFormatException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.IO.FileLoadException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.IO.FileNotFoundException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.IO.IOException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.IO.InternalBufferOverflowException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.IO.InvalidDataException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.IO.IsolatedStorage.IsolatedStorageException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.IO.PathTooLongException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.InsufficientExecutionStackException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.InsufficientMemoryException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Int16?displayProperty=nameWithType> | |
> | <xref:System.Int32?displayProperty=nameWithType> | |
> | <xref:System.Int64?displayProperty=nameWithType> | |
> | <xref:System.IntPtr?displayProperty=nameWithType> | |
> | <xref:System.InvalidCastException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.InvalidOperationException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.InvalidProgramException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.InvalidTimeZoneException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.MemberAccessException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.MethodAccessException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.MissingFieldException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.MissingMemberException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.MissingMethodException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.MulticastNotSupportedException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Net.Cookie?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieCollection?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieContainer?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Net.HttpListenerException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Net.Mail.SmtpException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Net.Mail.SmtpFailedRecipientException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Net.Mail.SmtpFailedRecipientsException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Net.NetworkInformation.NetworkInformationException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Net.NetworkInformation.PingException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Net.ProtocolViolationException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Net.Sockets.SocketException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Net.WebException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Net.WebSockets.WebSocketException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.NotFiniteNumberException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.NotImplementedException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.NotSupportedException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.NullReferenceException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Nullable%601?displayProperty=nameWithType> | |
> | <xref:System.Numerics.BigInteger?displayProperty=nameWithType> | |
> | <xref:System.Numerics.Complex?displayProperty=nameWithType> | |
> | <xref:System.Object?displayProperty=nameWithType> | |
> | <xref:System.ObjectDisposedException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.OperationCanceledException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.OutOfMemoryException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.OverflowException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.PlatformNotSupportedException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.RankException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Reflection.AmbiguousMatchException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Reflection.CustomAttributeFormatException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Reflection.InvalidFilterCriteriaException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Reflection.ReflectionTypeLoadException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4.<br/>La sérialisation de .NET Framework à .NET Core n’est pas prise en charge. |
> | <xref:System.Reflection.TargetException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Reflection.TargetInvocationException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Reflection.TargetParameterCountException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Resources.MissingManifestResourceException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Resources.MissingSatelliteAssemblyException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Runtime.CompilerServices.RuntimeWrappedException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Runtime.InteropServices.COMException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Runtime.InteropServices.ExternalException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Runtime.InteropServices.InvalidComObjectException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Runtime.InteropServices.InvalidOleVariantTypeException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Runtime.InteropServices.MarshalDirectiveException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Runtime.InteropServices.SEHException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Runtime.Serialization.InvalidDataContractException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Runtime.Serialization.SerializationException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.SByte?displayProperty=nameWithType> | |
> | <xref:System.Security.AccessControl.PrivilegeNotHeldException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Security.Authentication.AuthenticationException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Security.Authentication.InvalidCredentialException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Security.Cryptography.CryptographicException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Security.Cryptography.CryptographicUnexpectedOperationException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | `System.Security.Cryptography.Xml.CryptoSignedXmlRecursionException` | À partir de .NET Core 2.0.4. |
> | <xref:System.Security.HostProtectionException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Security.Policy.PolicyException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Security.Principal.IdentityNotMappedException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Security.SecurityException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4.<br/>Données de sérialisation limitées. |
> | <xref:System.Security.VerificationException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Security.XmlSyntaxException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.ServiceProcess.TimeoutException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Single?displayProperty=nameWithType> | |
> | <xref:System.StackOverflowException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.String?displayProperty=nameWithType> | |
> | <xref:System.StringComparer?displayProperty=nameWithType> | |
> | <xref:System.SystemException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Text.DecoderFallbackException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Text.EncoderFallbackException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Text.RegularExpressions.RegexMatchTimeoutException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Text.StringBuilder?displayProperty=nameWithType> | |
> | <xref:System.Threading.AbandonedMutexException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Threading.BarrierPostPhaseException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Threading.LockRecursionException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Threading.SemaphoreFullException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Threading.SynchronizationLockException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Threading.Tasks.TaskSchedulerException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Threading.ThreadInterruptedException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Threading.ThreadStartException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Threading.ThreadStateException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Threading.WaitHandleCannotBeOpenedException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.TimeSpan?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneNotFoundException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.TimeoutException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Transactions.TransactionAbortedException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Transactions.TransactionException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Transactions.TransactionInDoubtException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Transactions.TransactionManagerCommunicationException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Transactions.TransactionPromotionException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Tuple?displayProperty=nameWithType> | |
> | <xref:System.TypeAccessException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.TypeInitializationException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.TypeLoadException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.TypeUnloadedException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.UInt16?displayProperty=nameWithType> | |
> | <xref:System.UInt32?displayProperty=nameWithType> | |
> | <xref:System.UInt64?displayProperty=nameWithType> | |
> | <xref:System.UIntPtr?displayProperty=nameWithType> | |
> | <xref:System.UnauthorizedAccessException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Uri?displayProperty=nameWithType> | |
> | <xref:System.UriFormatException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.ValueTuple?displayProperty=nameWithType> | Non sérialisable dans .NET Framework 4,7 et versions antérieures. |
> | <xref:System.ValueType?displayProperty=nameWithType> | |
> | <xref:System.Version?displayProperty=nameWithType> | |
> | <xref:System.WeakReference%601?displayProperty=nameWithType> | |
> | <xref:System.WeakReference?displayProperty=nameWithType> | |
> | <xref:System.Xml.Schema.XmlSchemaException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Xml.Schema.XmlSchemaInferenceException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Xml.Schema.XmlSchemaValidationException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Xml.XPath.XPathException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Xml.XmlException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Xml.Xsl.XsltCompileException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |
> | <xref:System.Xml.Xsl.XsltException?displayProperty=nameWithType> | À partir de .NET Core 2.0.4. |

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization>\
Contient des classes qui peuvent être utilisées pour sérialiser et désérialiser des objets.

- [Sérialisation XML et SOAP](xml-and-soap-serialization.md)\
Décrit le mécanisme de sérialisation XML inclus avec le Common Language Runtime.

- [Sécurité et sérialisation](../../framework/misc/security-and-serialization.md)\
Décrit les indications de codage sécurisé à suivre lors de l'écriture du code qui exécute la sérialisation.

- [.NET Remoting](/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))\
Décrit les différentes méthodes à partir de .NET Framework pour les communications à distance.

- [Services Web XML créés à l’aide des clients de service Web XML et ASP.NET](/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))\
Articles qui décrivent et expliquent comment programmer des services Web XML créés à l’aide de ASP.NET.
