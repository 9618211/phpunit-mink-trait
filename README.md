# phpunit-mink-trait

Trait that provides minimal integration layer for using Mink in PHPUnit test cases

## Installation

To add this component as a local, per-project dependency to your project, simply add a dependency on `sebastian/phpunit-mink-trait` to your project's `composer.json` file. Here is a minimal example of a `composer.json` file that just defines a dependency on this component:

```JSON
{
    "require": {
        "sebastian/phpunit-mink-trait": "~1.0"
    }
}
```

## Usage

```php
<?php
class ExampleTest extends PHPUnit_Framework_TestCase
{
    use phpunit\mink\TestCaseTrait;

    public function testHasCorrectTitle()
    {
        $page = $this->visit('http://example.com/');

        $this->assertContains(
            'Example Domain', $page->find('css', 'title')->getHtml()
        );
    }

    public function testMoreInformationCanBeAccessed()
    {
        $page = $this->visit('http://example.com/');
        $page->clickLink('More information...');

        $this->assertContains(
            'IANA', $page->find('css', 'title')->getHtml()
        );
    }
}
```

