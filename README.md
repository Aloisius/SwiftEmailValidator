![swift workflow](https://github.com/ekscrypto/SwiftEmailValidator/actions/workflows/swift.yml/badge.svg) [![codecov](https://codecov.io/gh/ekscrypto/SwiftEmailValidator/branch/main/graph/badge.svg?token=W9KO1BG8S0)](https://codecov.io/gh/ekscrypto/SwiftEmailValidator) [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) ![Issues](https://img.shields.io/github/issues/ekscrypto/SwiftEmailValidator) ![Releases](https://img.shields.io/github/v/release/ekscrypto/SwiftEmailValidator)

# SwiftEmailValidator

A Swift implementation of an international email address syntax validator as per RFC5321. Since email addresses are 
local @ remote the validator also includes IPAddressSyntaxValidator and EmailHostSyntaxValidator classes.  This 
Swift Package does not require an Internet connection at runtime and is entirely self contained.

RFC5321 - Simple Mail Transfer Protocol
https://datatracker.ietf.org/doc/html/rfc5321

Domains are validated against the Public Suffix List at https://publicsuffix.org . To update the built-in suffix list
(PublicSuffixRulesRegistry.swift) use the Utilities/update-suffix.swift script.

Public Suffix List last updated on 2022-01-22

## IPAddressSyntaxValidator

    if IPAddressSyntaxValidator.matchIPv6("::1") {
        print("::1 is a valid IPv6 address")
    }

    if IPAddressSyntaxValidator.matchIPv4("127.0.0.1") {
        print("127.0.0.1 is a valid IPv4 address")
    }
    
    if IPAddressSyntaxValidator.match("8.8.8.8") {
        print("8.8.8.8 is a valid IP address")
    }
    
    if IPAddressSyntaxValidator.match("fe80::1") {
        print("fe80::1 is a valid IP address")
    }


## EmailHostSyntaxValidator
Validates if the email's host name is following expected syntax rules and whether it is part of a known public suffix. Does NOT validate if the domain actually exists or even allowed by the registrar.

    if EmailHostSyntaxValidator.match("yahoo.com") {
        print("yahoo.com has valid email host syntax")
    }
