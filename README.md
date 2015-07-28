# Introduction

["Pact"](https://github.com/realestate-com-au/pact) is an implementation of "consumer driven contract" testing that allows mocking of responses in the consumer codebase, and verification of the interactions in the provider codebase. The initial implementation was written in Ruby for Rack apps, however a consumer and provider may be implemented in different programming languages, so the "mocking" and the "verifying" steps would be best supported by libraries in their respective project's native languages. Given that the pact file is written in JSON, it should be straightforward to implement a pact library in any language, however, to get the best experience and most reliability of out mixing pact libraries, the matching logic for the requests and responses needs to be identical. There is little confidence to be gained in having your pacts "pass" if the logic used to verify a "pass" is inconsistent between implementations.

To support consistency of matching logic, this specification has been developed as a benchmark that all pact libraries can check themselves against if they want to ensure consistency with other pact libraries.

### Pact Specification Philosophy

* Be as strict as we reasonably can with what we send out (requests). We should know and be able to control exactly what a consumer is sending out. Information should not be allowed to "leak" silently.
* Be as loose as we reasonably can with what we accept (responses). A provider should be able to send extra information that this particular consumer does not care about, without breaking this consumer.
* When writing the matching rules, err on the side of being more strict now, because it will break fewer things to be looser later, than to get stricter later.

Note: One implications of this philosophy is that you cannot verify, using pact, that a key or a header will _not_ be present in a response. You can only verify what _is_.

### Version 3.0 (WIP)

Version 3.0 introduces the following changes from 2.0:

#### Introduces messages for services that communicate via event streams and message queues

#### Query strings are stored as Map instead of strings

#### Allow multiple provider states with parameters

#### Allow arrays of matchers to be defined against a matcher path

#### Allow schemas to be defined

#### Matching times and dates in a cross-platform manner

### References

* https://groups.google.com/forum/#!topic/pact-dev/T3TYHJWWw2c
* https://github.com/DiUS/pact-jvm/issues/97
* https://groups.google.com/forum/#!topic/pact-support/d0nXzVi1Nf0
* https://groups.google.com/forum/#!topic/pact-support/YHw7hgD1d4g
