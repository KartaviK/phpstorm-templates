# Files/snippets templates for PhpStorm

## PHP

### Class (file)

```php
<?php
#if (${NAMESPACE})

namespace ${NAMESPACE};
#end

/**
 * Class ${NAME}
 * @package ${NAMESPACE}
 */
class ${NAME}
{

}

```

### Interface (file)

```php
<?php
#if (${NAMESPACE})

namespace ${NAMESPACE};
#end

/**
 * Interface ${NAME}
 * @package ${NAMESPACE}
 */
interface ${NAME}
{

}

```

### Trait (file)

```php
<?php
#if (${NAMESPACE})

namespace ${NAMESPACE};
#end

/**
 * Trait ${NAME}
 * @package ${NAMESPACE}
 */
trait ${NAME}
{

}

```

### Unit 6 (file)

```php
<?php
#if (${NAMESPACE})

namespace ${NAMESPACE};
#end

#if (${TESTED_NAME} && ${NAMESPACE} && !${TESTED_NAMESPACE})
use ${TESTED_NAME};
#elseif (${TESTED_NAME} && ${TESTED_NAMESPACE} && ${NAMESPACE} != ${TESTED_NAMESPACE})
use ${TESTED_NAMESPACE}\\${TESTED_NAME};
#end

use PHPUnit\Framework\TestCase;

/**
 * Class ${NAME}
 * @package ${NAMESPACE}
 * @coversDefaultClass ${TESTED_NAME}
 * @internal
 */
class ${NAME} extends TestCase
{
    /** @var ${TESTED_NAME} */
    protected ${DS}fake${TESTED_NAME};

    protected function setUp(): void
    {
        ${DS}this->fake${TESTED_NAME} = new ${TESTED_NAME}();
    }
}

```

### Custom Exception (file)

```php
<?php
#set ($VARIABLES = $INPUT.split(","))
#set (${VARIABLE} = "")
#set (${REST} = "")

#if (${NAMESPACE})
namespace ${NAMESPACE};
#end

/**
 * Class ${NAME}
 * @package ${NAMESPACE}
 */
class ${NAME} extends \Exception
{
    #foreach (${VARIABLE} in $VARIABLES)
    #set ($SEPARATED = $VARIABLE.split(" "))
    #if ($SEPARATED.size() == 2)
    /** @var $SEPARATED.get(0)|null */
    protected ${DS}$SEPARATED.get(1);

    #else
    protected ${DS}$SEPARATED.get(0);
    
    #end
    #end
    public function __construct(
        #foreach (${VARIABLE} in $VARIABLES)
        #set ($SEPARATED = $VARIABLE.split(" "))
        #if ($SEPARATED.size() == 2)
        $SEPARATED.get(0) ${DS}$SEPARATED.get(1) = null,
        #else
        ${DS}$SEPARATED.get(0) = null,
        #end
        #end
        string ${DS}message = "",
        int ${DS}code = 0,
        \Throwable ${DS}previous = null
    ) {
        #foreach (${VARIABLE} in $VARIABLES)
        #set ($SEPARATED = $VARIABLE.split(" "))
        #if ($SEPARATED.size() == 2)
        ${DS}this->$SEPARATED.get(1) = ${DS}$SEPARATED.get(1);
        #else
        ${DS}this->$SEPARATED.get(0) = ${DS}$SEPARATED.get(0);
        #end
        #end
    
        parent::__construct(${DS}message, ${DS}code, ${DS}previous);
    }
    #foreach (${VARIABLE} in $VARIABLES)

    #set($SEPARATED = $VARIABLE.split(" "))
    #if ($SEPARATED.size() == 2)
    #set ($VAR = $SEPARATED.get(1))
    #set($FIRST_LETTER = $VAR.substring(0, 1).toUpperCase())
    #set($REST = $VAR.substring(1))
    public function get${FIRST_LETTER}${REST}(): ?$SEPARATED.get(0)
    {
        return ${DS}this->$VAR;
    }
    #else
    #set($FIRST_LETTER = $SEPARATED.get(0).substring(0, 1).toUpperCase())
    #set($REST = $SEPARATED.get(0).substring(1))
    public function get${FIRST_LETTER}${REST}()
    {
        return ${DS}this->$SEPARATED.get(0);
    }
    #end
    #end
}

```

#### Rules

- in menu you must choose `new => PHP Class`
- between type and variable separator: `" "`
- between arguments separator: `","`
- nothing must be between arguments if type is not set

#### Example

- NAME: `InvalidArgumentsException`
- NAMESAPCE: `Project\Exceptions`
- INPUT: `string arg1,int arg2,arg3`

Output:

```php
<?php

namespace Project\Exceptions;

/**
 * Class InvalidArgumentsException
 * @package Project\Exceptions
 */
class InvalidArgumentsException extends \Exception
{
    /** @var string|null */
    protected $arg1;

    /** @var int|null */
    protected $arg2;

    protected $arg3;

    public function __construct(
        string $arg1 = null,
        int $arg2 = null,
        $arg3 = null,
        string $message = "",
        int $code = 0,
        \Throwable $previous = null
    )
    {
        $this->arg1 = $arg1;
        $this->arg2 = $arg2;
        $this->arg3 = $arg3;

        parent::__construct($message, $code, $previous);
    }

    public function getArg1(): ?string
    {
        return $this->arg1;
    }

    public function getArg2(): ?int
    {
        return $this->arg2;
    }

    public function getArg3()
    {
        return $this->arg3;
    }
}

```

### Array (file)

```php
<?php

return [
    
];

```

### Getter (snippet)

```php
public ${STATIC} function ${GET_OR_IS}${NAME}()#if(${RETURN_TYPE}): ${RETURN_TYPE}#else#end
{
#if (${STATIC} == "static")
    return self::$${FIELD_NAME};
#else
    return $this->${FIELD_NAME};
#end
}

```

### Unit 6 test method (snippet) (php 7.1+)

```php
public function test${CAPITALIZED_NAME}(): void
{

}
```

### Unit 6 test method (snippet) (php 7.1-)

```php
public function test${CAPITALIZED_NAME}()
{

}
```

### Public constant (snippet) (php 7.1+)

```php
public const $NAME$ = $VALUE$;$END$
```

### Protected contant (snippet) (php 7.1+)

```php
protected const $NAME$ = $VALUE$;$END$
```

### Private constant (snippet) (php 7.1+)

```php
private const $NAME$ = $VALUE$;$END$
```

### Constant (snippet) (php 7.1-)

```php
const $NAME$ = $VALUE$;$END$ 
```
