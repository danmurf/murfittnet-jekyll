---
layout: post
title:  "CodeIgniter Math CAPTCHA library, with multi-language plain text questions"
date:   2012-09-09 14:02:00 +0000
tags: [ Security, PHP, CodeIgniter ]
permalink: blog/codeigniter-math-captcha-library-multi-language-plain-text-questions
---
<a href="http://www.flickr.com/photos/96khz/3127953038/" title="Robot by Sebastianlund, on Flickr"><img src="http://farm4.staticflickr.com/3085/3127953038_e8484f17b8_m.jpg" style="height:240px; width:172px; float:right; margin:5px 20px;" alt="Robot"></a>

I've just released a new Math CAPTCHA Library for CodeIgniter, which can use plain text English words for numbers and random question phrases. It's also supports multiple languages (as it uses the core language library) and both addition and multiplication. It's still in the early stages so it needs to be put through its paces, but hopefully the CodeIgniter community will find this a nice alternative to the regular image CAPTCHA or simple math CAPTCHA.

The library comes with 5 English language phrases and English numerals, but can easily be set up to use any other language by replicating and translating the language file. Users are also encouraged to enter their own phrases (as many as you like) in order to make the CAPTCHA more random. The phrases are randomly selected. 

For example:

> What do you get if you add eight to five?

Or if you'd prefer to have numbers in the phrase:

> What is 7 plus 6?

Or mix it up:

>  Add 10 to ten, what do you get?

Answers can be enforced to either number only, word only, or either.

##Where can I find it?

Head over to GitHub to view/download the latest development version and start testing: 

<https://github.com/danmurf/CI-MathCaptcha>

Any comments and suggestions welcome :)

##Installation

The folder structure should match the CodeIgniter folder structure.

###Quick setup

*   Copy the `application/libraries/mathcaptcha_library.php` file to `application/libraries/`
*   Copy the `application/language/english/mathcaptcha_lang.php` to `application/language/english/`
*   If you would like to use another language other than English you will need to duplicate the language file and translate the numbers and phrases respectively
*   Initialise the math CAPTCHA library and include it in your controller. Example below:

```php
public function myform()
{
        $this->load->library('mathcaptcha');
        $this->mathcaptcha->init();
            
        $data['math_captcha_question'] = $this->mathcaptcha->get_question();
            
        $this->form_validation->set_rules('math_captcha', 'Math CAPTCHA', 'required|callback__check_math_captcha');
            
        if ($this->form_validation->run() == FALSE)
        {
            $this->load->view('myform', $data);
        }
        else
        {
            $this->load->view('myform', $data);
        }
}
```

*   Add a callback for the math CAPTCHA form validation if you are using CodeIgniter Form Validation library. Example below:

```php   
function _check_math_captcha($str)
{
    if ($this->mathcaptcha->check_answer($str))
    {
        return TRUE;
    }
    else
    {
        $this->form_validation->set_message('_check_math_captcha', 'Enter a valid math captcha response.');
        return FALSE;
    }
}
```

*   Print the `$mathcaptcha_question` on your form somewhere. Example below:

```php
<?php echo validation_errors(); ?>
  
<?php echo form_open(); ?>
  
    <?php echo $math_captcha_question;?>
    
    <?php echo form_input('math_captcha');?>
    
    <?php echo form_submit('submit', 'Submit'); ?>
    
<?php echo form_close();?>
```

*   And that's it!

##Configuration options

There are some configuration options which you can pass to the library in an associative array when you `$this->mathcaptcha->init($config)`:

*   **language**: This should be set to the language that you want to use. It will default to the language set in the Codeigniter `config.php`.
*   **operation**: The type of math question to use; `addition` or `multiplication`. This will default to `addition` if not specified.
*   **question_format**: The type of number to include in the question; `numeric`, `word`, or `random`. This will default to `word` if not specified.
*   **question_max_number_size**: The maximum number size to use in the question. The default is `10`, which is also the maximum allowed given the limitations of the language file.
*   **answer_format**: The type of answer that is allowed; `word` means the user must answer in a word, `numeric` means the user must enter the number or `either` for, well, either.

In order to make your installation of math CAPTCHA more unique you can try changing/adding more phrases to the language file. If you add more than 5, adjust the `MATHCAPTCHA_NUM_ADDITION_PHRASES` and `MATHCAPTCHA_NUM_MULTIPLICATION_PHRASES` constants in the library file appropriately.

**Photo credit**: Robot by Sebastian Lund on Flickr: <http://www.flickr.com/photos/96khz/3127953038/>