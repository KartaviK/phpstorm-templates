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
