# Files/snippets templates for PhpStorm

## PHP

### PHP Class (file)

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

### PHP Interface (file)

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

### PHP Trait (file)

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

### PHPUnit 6 (file)

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

}

```

### PHP Array (file)

```php
<?php

return [
    ${END}
];

```

### PHP Getter (snippet)

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

### PHPUnit test method (snippet)

```php
public function test${CAPITALIZED_NAME}(): void
{

}
```
