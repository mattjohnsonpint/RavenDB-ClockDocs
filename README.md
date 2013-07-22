ClockDocs Bundle for RavenDB
=====================================

This is a custom bundle for RavenDB.  The current release requires RavenDB version 2.0.2261 or higher.

It keeps the current time updated periodically in RavenDB system documents, so that you can join to them in indexes with `LoadDocument`.

Full documentation is pending.  Please review the unit tests for example usage.

### Performance Impact

While this bundle *works*, there has been some discussion in the user group about performance problems that might be encountered when using this approach.
If you have a relatively small number of documents to update, you should be fine.  But the current advice is to avoid using this with anything that might have 10,000 or more documents linked to a single ClockDoc.
Doing so will put a very high burden on updating indexes, and could certainly lead to production failures.

Please consider this bundle as *expiremental*.  Test thoroughly, under similar conditions as you might find in your production environment.

### Installation

- Download the source and compile.
- Place the `Raven.Bundles.ClockDocs.dll` file in your plugins directory.
- Reference the `Raven.Client.Bundles.ClockDocs.dll` file from your client project.
- In embedded mode, reference *both* dlls.
- See the unit tests for configuration and usage examples.
