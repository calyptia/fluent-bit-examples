## Description
Oracle WebLogic is a Java Enterprise Edition (JEE) Application Server developed by Oracle Corporation. Logging related documentation, including example logs as well as log locations can be found from in the following: https://docs.oracle.com/cd/E23943_01/web.1111/e13739/logging_services.htm#WLLOG123


## Example Log
```
<Sept 22, 2004 10:51:10 AM EST> <Notice> <WebLogicServer> <BEA-000360> <Server started in RUNNING mode>
```

The following example log includes the following parameters. If you are using a different format for your Oracle WebLogic logs be sure to adjust to parser below: 
* Locale-formatted Timestamp
* Severity
* Subsystem
* MessageID
* MessageText

## Example Parser

https://rubular.com/r/eDjh4VKFhZ6gbO

```
^\<(?<time>[^\>]+)\> \<(?<severity>[^ ]+)\> \<(?<subsystem>[^ ]+)\> \<(?<message-id>[^ ]+)\> \<(?<message>[^\>]+)\>
```

| Fields | Data |
| ---- | ---- |
| time | Sept 22, 2004 10:51:10 AM EST |
| severity |	 Notice |
| subsystem |	WebLogicServer |
| message-id |	BEA-000360 |
| message |	Server started in RUNNING mode |

```
Time format %b %d, %Y %I:%M:%S %p %Z
```

## Example Configuration
The following configuration can be used when reading the logs from tail. Other potential ways of sending logs from Oracle WebLogic include using Log4J to syslog, however this is outside the scope of this document.

## Fluentd 1.0+ Example

[Tail documentation](https://docs.fluentd.org/input/tail)
```
<source>
  @type tail
  path /var/log/foo/bar.log
  pos_file /var/log/td-agent/foo-bar.log.pos
  tag foo.bar
  <parse>
    @type regexp
    expression /^\<(?<time>[^\>]+)\> \<(?<severity>[^ ]+)\> \<(?<subsystem>[^ ]+)\> \<(?<message-id>[^ ]+)\> \<(?<message>[^\>]+)\>/
    time_format %b %d, %Y %I:%M:%S %p %Z
  </parse>
</source>
```

## Fluent Bit 1.6+ Example
With Fluent Bit you will need to define a Parser and an Input plugin. Pre-defined parsers can be found in `/etc/td-agent-bit/parsers.conf`

[Parse documentation](https://docs.fluentbit.io/manual/pipeline/parsers/regular-expression)
[Tail documentation](https://docs.fluentbit.io/manual/pipeline/inputs/tail)
```
[PARSER]
    Name weblogic
    Format regex
    Regex /^\<(?<time>[^\>]+)\> \<(?<severity>[^ ]+)\> \<(?<subsystem>[^ ]+)\> \<(?<message-id>[^ ]+)\> \<(?<message>[^\>]+)\>/
    Time_Key time
    Time_Format %b %d, %Y %I:%M:%S %p %Z
```    
```
[INPUT]
    Type tail
    Path /var/log/foo/bar.log
    Parser weblogic
    Tag weblogic
```
