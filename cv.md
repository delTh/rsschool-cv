# Alex Ponomarev

**email: yadelth@ya.ru**

**github: @delth**
_________________________
## About me

Hello and welcome!  
I`m middle php developer. My interests include js web develop, UX design and other creative stuff.

-------------------------
## Сourses

 - [Web технологии](https://github.com/delTh/web_tech) 
 - ["Разработка веб сервиса" на Stepic.org](https://github.com/delTh/stepic_java) 

## My Certificate

![Web технологии](https://github.com/delTh/rsschool-cv/raw/gh-pages/images/2022-12-10_21-18-49.png) 
![Разработка веб сервиса на Java (часть 1)](https://github.com/delTh/rsschool-cv/raw/gh-pages/images/2022-12-10_21-20-05.png) 
![Разработка веб сервиса на Java (часть 2)](https://github.com/delTh/rsschool-cv/raw/gh-pages/images/2022-12-10_21-20-53.png) 

## Example code 

```
namespace Fbit\SoapService\Services\LogService;

use Fbit\SoapService\Config;
use Monolog\Logger as MonologLogger;
use Monolog\Formatter\LineFormatter;
use Monolog\Handler\RotatingFileHandler;
use Monolog\Registry;
use Exception;


final class Logger {
    
    /**
     *  Logger
     *
     * @param string $name
     * @return MonologLogger
     */
    
    public static function getInstance( string $name =  'main' ): MonologLogger {
        
        if ( Registry::hasLogger( $name )) {
            return Registry::getInstance( $name );
        }
        
        $logger = new MonologLogger( $name );
        $path = $_SERVER["DOCUMENT_ROOT"]. Config::ENV_LOG_DIRECTORY() .  '/' . $name . '.log';
        $handler = new RotatingFileHandler($path, Config::ENV_MAX_FILES());
        $handler->setFormatter(new LineFormatter());
        $handler->setLevel(Config::ENV_LOG_LEVEL());
    
        $logger->pushHandler( $handler );
        Registry::addLogger($logger, $name);
        return $logger;
    }    
}
```





