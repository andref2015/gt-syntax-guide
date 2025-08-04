# GUIDEDTRACK SYNTAX GUIDE

GuidedTrack is a strict programming language. Always refer to this guide whenever attached. Read ALL of it VERY carefully.

This syntax guide helps AI assistants understand and write GuidedTrack code. If you find errors, better syntax approaches, or new insights about the language, update this guide—but ask the user permission first. 

## Table of Contents

### Part 1: Fundamentals
- [What is GuidedTrack](#what-is-guidedtrack)
- [Basic Syntax Rules](#basic-syntax-rules)
- [Code Organization](#code-organization)
- [Debugging](#debugging)
- [Critical Rules Summary](#critical-rules-summary)

### Part 2: Basic Programming
- [Text Display & Formatting](#text-display--formatting)
- [Lists](#lists)
- [Variables & Operations](#variables--operations)
- [Buttons](#buttons)
- [Collections & Dictionaries](#collections--dictionaries)
- [Subprograms](#subprograms)
- [Media (Images, Video, Audio)](#media-images-video-audio)
- [Utility Programs](#utility-programs)

### Part 3: Questions
- [Basic Questions](#basic-questions)
- [Question Types & Keywords](#question-types--keywords)
- [Question Tags and Rules](#question-tags-and-rules)
- [Data::store](#datastore)
- [Throwaway](#throwaway)

### Part 4: Flow Control
- [Conditional Logic](#conditional-logic)
- [Navigation](#navigation)
- [Loops](#loops)
- [Randomization & Experiments](#randomization--experiments)
- [Screen and Execution Control](#screen-and-execution-control)

### Part 5: HTML & CSS
- [Basic HTML/CSS Usage](#basic-htmlcss-usage)
- [Interactive Components](#interactive-components)
- [Common Reusable Patterns](#common-reusable-patterns)
- [CSS Best Practices & Troubleshooting](#css-best-practices--troubleshooting)
- [Clearer Thinking Color Palette](#clearer-thinking-color-palette)

### Part 6: Advanced Features
- [Email](#email)
- [Time & Calendar](#time--calendar)
- [Charts](#charts)
- [Navigation Menu](#navigation-menu)
- [Back Button & Points](#back-button--points)
- [Page & Login](#page--login)
- [API Calls & Services](#api-calls-&-services)

### Part 7: Best Practices & Reference
- [Coding Principles](#coding-principles)
- [Error Prevention](#error-prevention)
- [Our Work Ecosystem](#our-work-ecosystem)

<br>

# Part 1: Fundamentals

## What is GuidedTrack

GuidedTrack is a programming language for creating surveys, experiments, and interactive web applications. Programs run on guidedtrack.com and can be embedded on other websites.
- Programs execute line by line until reaching a "page break"
- Page breaks occur at: *button, *question, or infinite *wait
- Variables persist across pages throughout the program
- All user responses and variables are automatically saved to a CSV file, regardless of whether the program completes
- Any variable you create in your program will automatically appear as a column in the CSV file when you download the data
- The column name will be the variable name

## Basic Syntax Rules

**⚠️ CRITICAL RULES**
- **ALWAYS use TABS for indentation.** NEVER use spaces for indentation. Incorrect indentation (using spaces) WILL break your program.
- **Comments must be on separate lines** starting with `--`. NEVER add comments at the end of code lines - this will break your program. This rule also applies to ALL code examples in this syntax guide - never show inline comments in examples.

**Other Important Rules:**
- Variable names are case-sensitive
- HTML styling (CSS) resets after every page break
- Strings must be written in a single line (no triple quotes)
- GuidedTrack starts indexing lists/collections with the value 1, NOT 0
- Syntax is strict, do not infer new syntax from other languages (except CSS styling in `*html` blocks)

## Code Organization

Use comments to organize sections, like the following:

```guidedtrack
----------------------------------
-- Section Name
----------------------------------
```

For individual questions or small sections, prefer single-line comments:
```guidedtrack
-- Question 1: Pattern Recognition
*question: What comes after: 2, 3, 4...

-- Question 2: Mathematical reasoning
```

Inside comments, uppercase words followed by `:` appear orange in the GuidedTrack online code editor
```guidedtrack
-- IMPORTANT: WARNING:
-- Developer X is debugging this page right now, so please don't make edits
```


## Debugging

**Display variable values:**
```guidedtrack
*if: debugMode
	userName = {userName}
```

**Show collection contents:**
```guidedtrack
*if: debugMode
	*for: item in myList
		Item: {item}
```

## Critical Rules Summary

**Essential Rules:**
- Use TABS for indentation (never spaces)
- Comments on separate lines only
- Arrays/lists are 1-indexed
- HTML/CSS resets after page breaks
- Each `*html` block must be self-contained
- No JavaScript (use `*component` with `*click`)
- Use `!important` in all CSS
- `*button` stops execution until clicked
- Cannot use `==` for comparison (use single `=`)
- Only the user can run/debug programs in the browser

**Common Pitfalls:**
- Forgetting variables persist but CSS doesn't
- Using `.length` instead of `.size` for arrays
- Opening HTML tags in one block, closing in another
- Using spaces for indentation
- Adding comments at end of code lines
- Forgetting to escape quotes in HTML strings
- Not targeting `p` elements for component text styling
- Not clearing heavy variables from csv after use
- Using `in` operator with strings (only works with collections/dictionaries)

<br>

# Part 2: Basic Programming

## Text Display & Formatting

**Basic text display:**
```guidedtrack
Hello world
You can also add emojis 😊
```

**Small line break:**
```guidedtrack
First line

Second line shown after a small line break
```

**Larger line break:**
```guidedtrack
*html
	<br>
```

**Double line break:**
```guidedtrack
*html
	<br><br>
```

**Comments:**
```guidedtrack
-- This line is a comment (NOT shown to user)
-- Comments must be on separate lines (NOT to the right of existing code)
```

**❌ WRONG:**
```guidedtrack
*for x in y -- this comment will break your program
```

**Text formatting:**
```guidedtrack
*Bold text*
/Italic text/
_Underlined text_
```

> **Note:** Must add spaces before/after formatting symbols, and no spaces between the symbols and the text they format. Default paragraph line height is 1.8; font-size 16px

**Basic header:**
```guidedtrack
*header: Section Title
```

**Hyperlinks:**
```guidedtrack
[Click here|https://example.com] to open a new tab and visit another website
```

## Lists

**Bullet points:**
```guidedtrack
*list
	Item 1
	Item 2
	Item 3
```

**Numbered list:**
```guidedtrack
*list: ordered
	First item
	Second item
```

**Expandable sections:**
```guidedtrack
*list: expandable
	Click to expand
		Hidden content here
```

## Variables & Operations

**Assign variables:**
```guidedtrack
>> variable_name = "value"
>> number = 42
>> is_active = 1
```

**String operations:**
```guidedtrack
>> userName = " Andre "
>> length = userName.size
>> upperName = userName.uppercase
>> lowerName = userName.lowercase
>> cleanedName = userName.clean
```

**Split text into a collection:**
```guidedtrack
>> my_text = "Hello World!"
>> words = my_text.split(" ")
```

**Encode and Decode text (useful for URLs):**
```guidedtrack
>> query = "name=John Doe"
>> encoded_query = query.encode("URL")
>> decoded_query = encoded_query.decode("URL")
```
> `encoded_query` is "name=John%20Doe"<br>
> `decoded_query` is "name=John Doe"

**String limitations:**
The `in` operator only works with arrays and dictionaries, not for checking if a substring exists within a string variable.

❌ WRONG:
```guidedtrack
*if: "cat" in "The cat is sleeping"
	This will cause an error
```

✅ CORRECT: Convert to collection first, then use "in"
```guidedtrack
>> words = response_riddle.split(" ")
*if: "cat" in words
	Found the word "cat"
```

✅ CORRECT: Use conditional logic for substring checking
```guidedtrack
*if: response_riddle = "cat"
	Exact match found
```

✅ CORRECT: For more flexible text matching, use utility programs:
```guidedtrack
>> in_textToEdit = user_input
>> in_textToReplace = "cat"
>> in_replacingText = "FOUND"
*program: replace text - public

*if: not (out_editedText = user_input)
	-- If text changed, then "cat" was found
	>> contains_cat = 1
```

> **Note:** The `in` operator only works with collections/arrays and dictionaries, NOT with strings for substring checking

**String concatenation:**
```guidedtrack
>> combined = "{variable1} and {variable2}"
```

**Math operations:**
```guidedtrack
>> sum = 5 + 3
>> product = 4 * 2
>> power = 2 ^ 3
>> squareRoot = 16 ^ 0.5
```

> **Note:** GuidedTrack lacks remainder syntax (NO % operator)

**Absolute value:**
```guidedtrack
>> number = -5
>> absolute_value = number
*if: number < 0
	>> absolute_value = -number
```

**Variables in text:**
```guidedtrack
My name is {userName}
You scored {score} points
```

## Buttons

**Basic button:**
```guidedtrack
*button: Click me!

This text only appears after the user clicks the button.
```

**CRITICAL: Code after `*button` only runs when clicked**
```guidedtrack
*button: Continue

>> this_runs_only_after_click = 1
This text appears only after button click.
```

**CRITICAL: Do NOT indent code right beneath button**
```guidedtrack
*button: Restart
	>> thisCausesError = 1
```

> **Important:** While `*button` creates page break, HTML custom buttons do NOT create a page break

## Collections & Dictionaries

### Collections (Arrays)

**Create collections:**
```guidedtrack
>> colors = ["red", "blue", "green"]
>> numbers = [1, 2, 3, 4, 5]
>> empty_list = []
```

**Access elements (1-indexed!):**
```guidedtrack
>> firstColor = colors[1]
>> lastNumber = numbers[numbers.size]
```

**Add elements:**
```guidedtrack
>> colors.add("yellow")
```

**Combine arrays:**
```guidedtrack
>> moreColors = ["pink", "white"]
>> colors.combine(moreColors)
```

**Check if item is in array:**
```guidedtrack
*if: "pink" in colors
	red is here!
```

**Find and count elements:**
```guidedtrack
>> my_collection = [10, 20, 30, 20]

-- Find the first position of an element (1-indexed)
>> position_of_20 = my_collection.find(20)
>> number_of_20s = my_collection.count(20)
```

**Remove elements:**
```guidedtrack
>> colors.erase("blue")

-- remove element by its index
>> colors.remove(2)
```

**Numerical collection methods:**
```guidedtrack
>> number_collection = [10, 5, 15, 5]
>> highest = number_collection.max
>> lowest = number_collection.min
>> average = number_collection.mean
>> middle_value = number_collection.median
```

**Other operations:**
```guidedtrack
>> colors.shuffle
>> sorted_numbers = numbers.sort("increasing")
>> sorted_numbers = numbers.sort("decreasing")
>> unique_items = numbers.unique
```

### Dictionaries (Associations)

**Create dictionaries:**
```guidedtrack
>> person = {"name" -> "John", "age" -> 25}
>> scores = {}
```

**Access/modify values:**
```guidedtrack
>> personName = person["name"]
>> person["age"] = 26
>> scores["player1"] = 100
>> person["sexiness"] = "high"
```

**Association methods:**
```guidedtrack
>> keys = person.keys
```
>`{keys}` = 'name, age, sexiness'

**Check if key exists:**
```guidedtrack
*if: "name" in person
	Name exists in the association
```

## Subprograms

**Call another program:**
```guidedtrack
*program: My Other Program
```

**Return from subprogram:**
```guidedtrack
*if: shouldExit = 1
	*return
```

**Switch vs Program:**
- `*program`: runs subprogram and returns automatically to parent once subprogram ends
- `*switch`: permanently switches to another program (no `*return` allowed)

## Media (Images, Video, Audio)

**Basic image (by default extends to full screen width):**
```guidedtrack
*image: https://example.com/image.jpg
```

**Image with caption:**
```guidedtrack
*image: https://example.com/image.jpg
	*caption: Description below image
	*description: Alt text for accessibility
```

**Video (also includes iframes):**
```guidedtrack
*video: https://example.com/video.mp4
```

**Audio:**
```guidedtrack
*audio: https://example.com/audio.mp3
```

## Utility Programs

**Random number between min and max:**
```guidedtrack
>> in_minValue = 1
>> in_maxValue = 10
*program: random integer between min and max - public
```

**Floor function:**
```guidedtrack
>> in_floor = 4.7
*program: floor - public
```

**Text replacement:**
```guidedtrack
>> in_textToEdit = "hello world"
>> in_textToReplace = " "
>> in_replacingText = "_"
*program: replace text - public
```

**Validate emails:**
```guidedtrack
*label: askEmail
*if: out_invalidEmail
    *if: out_invalidEmail = 1
        Sorry, you wrote an incorrect email.

*question: What is your email?
	*save: user_email

>> in_emailToCheck = user_email
*program: email format validation - public
*if: out_invalidEmail = 1
	*goto: askEmail
```

> **Note:** The first check for `out_invalidEmail` exists to avoid linter errors

**Sort names and values:**
```guidedtrack
-- Enter the collection of names to sort
>> in_namesToSort = ["Alice", "Bob", "Charlie", "David"]
-- Enter the collection of values to sort by
>> in_valuesToSortBy = [45, 16, 98, 34]
-- OPTIONAL: Set to "yes" to sort from lowest to highest (default is highest to lowest)
>> in_sortAscending = "no"

*program: sort names and values - public
-- outputs:
-- out_sortedNames
-- out_sortedValues
```

<br>

# Part 3: Questions

## Basic Questions

**Text input (1-line):**
```guidedtrack
*question: What is your name?
	*save: userName

This text appears only after answering question above.
```

**Multiple choice:**
```guidedtrack
*question: Choose your favorite color
	Red
	Blue
	Green
	*save: color
```

**Multiple choice with conditional logic:**
```guidedtrack
*question: Are you happy?
	Yes
		>> mood = "happy"
		Great!
	No
		>> mood = "sad"
		Sorry to hear that!
	*save: happyOrNot
```

**Show icons for options:**
```guidedtrack
*question: Choose one
	Stars
		*icon: fas fa-star
	Hearts
		*icon: fa-heart
	*save: choice
```

> **Allowed icons from:**
> - fontawesome.com/v5/search?m=free
> - getbootstrap.com/docs/3.3/components/#glyphicons

<br>

**Picture: show images in answer options:**
```guidedtrack
*question: Which image appeals to you?
	Nature Scene
		*picture: https://example.com/nature.jpg
	City View
		*picture: https://example.com/city.jpg
	*save: imageChoice
```

## Question Types & Keywords

**Allow blank responses (user can click "submit" without answering):**
```guidedtrack
*question: Optional comment
	*blank
	*save: comment
```

**Add placeholder text:**
```guidedtrack
*question: Enter email
	*placeholder: user@example.com
	*save: email
```

**Add tips (shown by default as text beneath the question):**
```guidedtrack
*question: Complex question
	*tip: Think carefully about this
	*save: answer
```

**Add before/after text:**
```guidedtrack
*question: Complete the sentence
	*before: I feel
	*after: today
	*save: feeling
```

**Add "Other" option (adds a line with "Other (please specify)"):**
```guidedtrack
*question: Favorite flavor?
	Chocolate
	Vanilla
	*other
	*save: flavor
```

**Countdown timer:**
```guidedtrack
*question: Quick! Capital of France?
	*countdown: 10.seconds
	*save: answer
```

**Allow multiple `*other` selections:**
```guidedtrack
*question: Favorite flavors? Select all
	*type: checkbox
	Chocolate
	Vanilla
	*other
	*save: flavors
```

**Confirm selection (user has to first select option and then also click "Next"):**
```guidedtrack
*question: Select carefully
	*confirm
	Option A
	Option B
	*save: choice
```

**Shuffle options:**
```guidedtrack
*question: Favorite animal
	*shuffle
	Cat
	Dog
	Donkey
	*save: favoriteAnimal
```

**Number input:**
```guidedtrack
*question: Enter your age:
	*type: number
	*save: age
```

**Paragraph input:**
```guidedtrack
*question: Describe your experience
	*type: paragraph
	*save: feedback
```

**Slider (default 0-100):**
```guidedtrack
*question: Rate your satisfaction
	*type: slider
	*save: satisfaction
```

**Slider input where you can select only integers (not decimals):**
```guidedtrack
*question: On a scale of 1-10, how much do you enjoy working with data?
	*answers: [1,2,3,4,5,6,7,8,9,10]
	*type: slider
	*save: data_enjoyment
```

**Slider with min and max:**
```guidedtrack
*question: Rate from 0-10
	*type: slider
	*min: 0
	*max: 10
	*save: rating
```
> **Note:** Allows to select every 0.10 digits (0.0, 0.1, 0.2, etc.) because GuidedTrack breaks down scale between min and max by 100

<br>

**Discrete slider with options:**
```guidedtrack
*question: How do you feel?
	*type: slider
	*save: mood
	Very sad
	Sad
	Neutral
	Happy
	Very happy
```

**Slider with encoded scale (users see text labels, CSV saves number):**
```guidedtrack
>> seatbeltScale = [["0% of the time", 0], ["10% of the time", 10], ["20% of the time", 20], ["30% of the time", 30], ["40% of the time", 40], ["50% of the time", 50], ["60% of the time", 60], ["70% of the time", 70], ["80% of the time", 80], ["90% of the time", 90], ["100% of the time", 100]]
*question: What percentage of the time do you wear a seatbelt in a car?
	*answers: seatbeltScale
	*type: slider
	*before: Never
	*after: Always
	*save: seatbelt_usage
```
> **Note:** `*before` and `*after` add fixed text labels to the left and right of the slider

<br>

**Define an answer scale to use in multiple questions:**
```guidedtrack
>> agreementScale = [["Totally agree", 3], ["Agree", 2], ["Somewhat agree", 1], ["Neither agree nor disagree", 0], ["Somewhat disagree", -1], ["Disagree", -2], ["Totally disagree", -3]]

*question: Is this demo useful?
	*answers: agreementScale
	*save: demoUsefulness

This is the encoded answer from your last question: {demoUsefulness}
```

> **Note:** User will see text options like "Totally agree" etc. but CSV saves encoded variables from -3 to +3

<br>

**Example of `*after` only:**
```guidedtrack
*question: How many times have you been arrested?
	*after: times
	*type: number
	*save: arrest_count
```

**Date input (asks both date and time):**
```guidedtrack
*question: When were you born?
	*type: calendar
	*save: birthDate
```

**Checkbox (multiple selection):**
```guidedtrack
*question: Select all that apply
	*type: checkbox
	Option A
	Option B
	Option C
	*save: selections
```

### Important Checkbox Rules

**CRITICAL**: Unlike regular multiple-choice type questions, checkbox questions cannot have code indented under options

**❌ WRONG:**
```guidedtrack
*question: Which traits best describe you? Select all that apply
	Detail-oriented
		>> analytical_score = analytical_score + 1 
	Creative
	*type: checkbox
```

**✅ CORRECT: For checkbox questions, handle scoring after the question**
```guidedtrack
*question: Which traits best describe you? Select all that apply
	Detail-oriented
	Creative
	*type: checkbox
	*save: selected_traits

*if: "Detail-oriented" in selected_traits
	>> analytical_score = analytical_score + 1
*if: "Creative" in selected_traits
	>> creative_score = creative_score + 1
```

**Question validation (ensuring exactly 2 selections):**
```guidedtrack
*label: vocab_question
*question: Select the *two* words that have the most similar meaning to each other:
	*type: checkbox
	*answers: ["Follower", "Gorge", "Companion", "Acolyte", "Leader"]
	*save: vocab_answer

*if: not vocab_answer.size = 2
	Please select exactly two words. Let's try again.
	*goto: vocab_question

*if: "Follower" in vocab_answer and "Acolyte" in vocab_answer
	>> vocabulary_score = 1
	Correct!
*if: not ("Follower" in vocab_answer and "Acolyte" in vocab_answer)
	>> vocabulary_score = 0
	Incorrect. The correct pair was Follower and Acolyte.
```

**Show checkbox question with options already pre-selected:**
```guidedtrack
*question: Which options do you want? Unselect those you don't want:
	*type: checkbox
	*default: ["Option A", "Option B"]
	Option A
	Option B
```

**Ranking (allows users to drag and drop items to rank them):**
```guidedtrack
*question: Rank these creatures from best to worst
	*type: ranking
	Tigers
	Bears
	Pigs
	Dragons
	*save: creature_ranking
```

> **Note:** Users can drag and drop the options to reorder them. GuidedTrack saves the result as an array in the user's preferred order.

**Multiple text inputs (allows users to enter multiple responses, one per row):**
```guidedtrack
*question: List your hobbies
	*multiple
	*save: hobbies
```

> **Note:** Users can add/remove rows and GuidedTrack saves all entries as an array
> **CRITICAL:** `*multiple` cannot be combined with `*type` modifiers (checkbox, number, etc.)

<br>

**Searchable dropdown:**
```guidedtrack
*question: Type then select your country
	*searchable
	United States
	Canada
	Mexico
	*save: country
```

> **Note:** `*searchable` does not allow `*type` configuration

<br>

## Question Tags and Rules

**Add question tags for summarizing responses later:**
```guidedtrack
*question: I enjoy public speaking.
	*tags: enjoys_public_speaking
	Yes
	No
	*save: public_speaking_score
```

**Use *summary to display questions and answers for a given tag:**
```guidedtrack
*summary: enjoys_public_speaking
```

### Dynamic Question Generation Rules

**CRITICAL: Cannot nest `*for` loops inside `*question` blocks to generate options**

**❌ WRONG:**
```guidedtrack
*question: What animal do you prefer?
	*for: animal in types_of_animals
		{animal}
	*save: preferences
```

**✅ CORRECT: Build options array first, then use in question as `*answers*`*
```guidedtrack
>> options = []
*for: animal in types_of_animals
	>> options.add(animal)
*question: What animal do you prefer?
	*answers: options
	*save: favoriteAnimal
```

**You can also nest questions:**
```guidedtrack
*question: What is your relationship status?
	Married
	Single
	Divorced
		*question: How many years ago did you divorce?
			*type: number
			*save: yearsAgoDivorce
	*save: relationshipStatus
```



## Data::store

Variables automatically save to CSV files:
- Column name = variable name  
- Use `data::store` for dynamic columns

**CRITICAL: Variable name interpolation is NOT supported - this will break the program:**
```guidedtrack
>> selectedTrait_{trait_id} = 1
```

### Problem: Loop data gets pipe-separated

```guidedtrack
*for: movie in movies
	*question: Rate {movie}?
		*answers: [1,2,3,4,5]
		*save: rating
```

> **Note:** The above creates a column named "Rate {movie}?" with pipe-separated ratings (e.g., "5|3|4"). The "rating" column only shows the last rating since its value gets overwritten in every iteration.

<br>

### Solution: Create separate columns

```guidedtrack
*for: movie in movies
	*question: Rate {movie}?
		*answers: [1,2,3,4,5]
		*save: rating
	>> data::store("rating_{movie}", rating)
```

> **Note:** The above creates separate columns: e.g., "rating_Titanic", "rating_Dune", etc.

<br>

## Throwaway

**Don't save the email to the CSV:**
```guidedtrack
*question: What's your email?
	*throwaway
	*save: tempEmail

*email
	*to: {tempEmail}
	*subject: Your Results
	*body
		Thank you! We haven't saved your email.

>> tempEmail = ""
```

> **Note:** The above will not save data in the 'What's your email?' CSV column, it will only save the 'tempEmail' variable

<br>

# Part 4: Flow Control

## Conditional Logic

**Basic comparisons:**
```guidedtrack
*if: age > 18
	You are an adult
*if: age <= 18
	You are not an adult!
```

> **Note:** When using an `*if` statement with an equal sign, make sure the variable being checked exists (otherwise it throws a linter error)

<br>

**String comparisons:**
```guidedtrack
*if: color = "red"
	You chose red!
*if: not (color = "red")
	You did not choose red!
```

**Variable existence checking:**
```guidedtrack
*if: userName
	You have entered your name!
*if: not userName
	You haven't entered your name yet
```

**Variable existence checking:**
```guidedtrack
*if: varCreated
	Run if variable was created previously in user's run
*if: not varCreated
	Run if variable was NEVER created previously by user

>> thisVarExists = 0
*if: thisVarExists
	This code will run!

>> alsoThisVarExists = ""
*if: alsoThisVarExists
	Also this code will run!
```

**Complex conditions:**
```guidedtrack
*if: age > 18 and hasLicense = 1
	You can drive

*if: score < 50 or timeUp = 1
	Game over
```

### Important Assignment Rules

**CRITICAL: You CANNOT directly assign comparison results to variables**

**❌ WRONG:**
```guidedtrack
>> is_correct = (user_answer = correct_answer)
>> is_same = variable1 = variable2
```

**✅ CORRECT: Use conditional assignment:**
```guidedtrack
*if: user_answer = correct_answer
	>> is_correct = 1
```

**CRITICAL: No `*elif` or `*else` statements exist**
- Use separate `*if` statements instead

## Navigation

**Labels and goto:**
```guidedtrack
*label: sectionName
*question: How are you?
	["Good", "Bad"]

*question: Re-answer previous question?
	Yes
		*goto: sectionName
	No
```

**Skip sections conditionally:**
```guidedtrack
*if: skipIntro = 1
	*goto: mainContent

-- Intro content here..

*label: mainContent
```

## Loops

**For loop through collections:**
```guidedtrack
*for: color in colors
	The color is {color}
```

**For loop with index:**
```guidedtrack
*for: index, item in myList
	Item {index}: {item}
```

**While loop:**
```guidedtrack
>> attempts = 0
*while: attempts < 3
	Attempt {attempts}
	>> attempts = attempts + 1
```

**Repeat fixed times:**
```guidedtrack
*repeat: 5
	This shows 5 times
```

## Randomization & Experiments

**Show one random option:**
```guidedtrack
*randomize
	You see option A
	You see option B
	You see option C
```

**Show multiple random options:**
```guidedtrack
*randomize: 2
	First possible item
	Second possible item
	Third possible item
```

**Show ALL questions in random order**
```guidedtrack
*randomize: all
	*question: What is 2+2?
		*type: number
	*question: What is 3+3?
		*type: number
```

**Re-randomize each time user runs this line of code:**
```guidedtrack
*randomize
	*everytime
	Option A
	Option B
```

**Random groups:**
```guidedtrack
*randomize
	*group
		>> group = "A"
		You're in group A
	*group
		>> group = "B"
		You're in group B
```

**Balanced experiment (same sample size per group, useful for A/B testing):**
```guidedtrack
*experiment: studyCondition
	*group
		>> condition = "control"
		Control group instructions
	*group
		>> condition = "treatment"
		Treatment group instructions
```

## Screen and Execution Control

**Wait:**
```guidedtrack
*wait: 2.seconds
```

**Sync data before proceeding (useful at end of Positly surveys):**
```guidedtrack
*wait: data
```

**Indefinite wait:**
```guidedtrack
*wait
```

> **Note:** Useful to create a page break without `*question`/`*button`, can be surpassed with a `*goto` and a `*label` after the `*wait`

<br>

**Maintain content across pages/questions:**
```guidedtrack
*maintain: These instructions stay visible
```

**Clear screen:**
```guidedtrack
*clear
```

> **Note:** Clears all text previously on screen and all `*maintain`

<br>

**Example of clear screen:**
```guidedtrack
Wait 2 seconds..
*wait: 2.seconds
*clear
Now you only see this!
```

**Progress bar:**
```guidedtrack
*progress: 50%
```

<br>

# Part 5: HTML & CSS

## Basic HTML/CSS Usage

**Styled headers (define CSS first, always resets after page break!):**
```guidedtrack
*html
	<style>
		.blue-color {
			color: #2196f3 !important;
		}
	</style>

*header: Blue Header
	*classes: blue-color
```

**Basic HTML:**
```guidedtrack
*html
	<div style="color: red !important;">Red text</div>
	<p>Paragraph with <strong>bold</strong> text</p>
```

**CSS styling:**
```guidedtrack
*html
	<style>
		.highlight {
			background-color: yellow !important;
			padding: 10px !important;
		}
	</style>

*html
	<div class="highlight">Highlighted text</div>
```

### Critical HTML Rules

**CRITICAL: GuidedTrack logic cannot be placed inside `*html` blocks**

All logic (variable assignments with `>>`, `*if` statements, etc.) must be processed *before* the `*html` block that might use the resulting variables. Data should be prepared in variables first, then interpolated into the HTML string.

**❌ WRONG:**
```guidedtrack
*html
	>> this_will_fail = "bad"
	<p>Test</p>
```

**✅ CORRECT:**
```guidedtrack
>> correct = "good"
*html
	<p>Value: {correct}</p>
```

**CRITICAL: Self-contained HTML blocks**
- Each `*html` block must be self-contained
- You CANNOT open tags in one block and close in another
- Use `*component` with `*classes` for styling containers around GuidedTrack elements
- Always use `!important` in CSS
- Cannot add JavaScript (NEVER use `onclick`, `addEventListener`, etc.)

**Advanced CSS limitations:**
- Some properties may get sanitized
- AVOID `backdrop-filter`, `-webkit-background-clip`, and complex `url()` backgrounds

**Link preferences:**
- Prefer GuidedTrack's native `[Link text|URL]` syntax over custom HTML `<a>` tags with styling
- Custom links are more likely to trigger linter errors

**Comment handling:**
- Comments within `<style>` tags are acceptable
- Comments (`<!-- ... -->`) within `*html` blocks can cause linter errors

**❌ WRONG:**
```guidedtrack
*html
	<!-- This comment will cause a linter error -->
```

**Ampersand escaping:**
- Unescaped ampersands (&) in HTML cause "unsafe markup" errors
- Always escape with `&amp;`

<br>

**❌ WRONG:**
```html
<h3>Quick & Engaging</h3>
```

**✅ CORRECT:**
```html
<h3>Quick &amp; Engaging</h3>
```

**Ampersands in href attributes cause linter errors:**

**❌ WRONG:**
```guidedtrack
*html
	<a href="http://amazon.com/product?ie=UTF8&camp=1789&creative=9325">Link</a>
```

**✅ CORRECT:**
```guidedtrack
>> book_url = "http://amazon.com/product?ie=UTF8&camp=1789&creative=9325"
*html
	<a href="{book_url}" target="_blank">Link</a>
```

**CSS Grid limitation:**
- `display: contents` BREAKS background gradients/colors
- This property removes the element from the layout tree, preventing background rendering

### HTML Examples

**Separate style blocks from content:**
```guidedtrack
*html
	<style>
		.my-styles {
			color: red !important;
		}
	</style>

*html
	<div class="my-styles">Content here</div>
```

**Default font-size note:**
- Do NOT specify "font-size: 16px" for `<p>` text as it's redundant (16px is default)

**HTML headers with custom styling:**
```guidedtrack
*html
	<h1 style="color: #2196f3;">Large Blue Header</h1>
	<h2 style="color: #ef4444;">Red Header</h2>
	<h4>Text in h4 tags is like normal text but larger</h4>
```

> **Note:** HTML styling resets after each page, so CSS classes must be redefined at the start of each new page. By default, `<h2>`, `<h3>`, and `<h4>` elements have #505050 as text color. `*header` elements (equivalent to `<h3>`) also have #505050 as default text color.

**Page numbers:**
```guidedtrack
*html
	<div class="right-aligned-italic">Page {currentPage} of {totalPageCount}</div>
```

**Programmable way to show images:**
```guidedtrack
>> imageToShow = "cat"
>> imageOfCat = "https://example.com/photos/{imageToShow}.jpeg"
*image: {imageOfCat}
```

> **Note:** GuidedTrack automatically adds borders to ALL `*components` - set "border: 0 !important;" to remove

<br>

## Interactive Components

Use `*component` with `*click` (NOT JavaScript!) - you need to define the HTML class first:

**Basic interactive component:**
```guidedtrack
*component
	*classes: my-button
	Click Me!
	*click
		>> clicked = 1
```

**Example: `*component` button does NOT stop execution**
```guidedtrack
*html
	<style>
		.custom-button {
			background: #2196f3 !important;
			padding: 6px 14px !important;
			border-radius: 6px !important;
			border: none !important;
			cursor: pointer !important;
			display: inline-block !important;
			width: fit-content !important;
		}
		.custom-button p {
			margin: 0 !important;
			font-weight: 500 !important;
			color: white !important;
		}
	</style>

*component
	*classes: custom-button
	Go to end
	*click
		>> button_clicked = 1
		*goto: endOfProgram

>> this_runs_immediately = 1
This text appears right beneath the button.
```

**Component with HTML content:**
```guidedtrack
*component
	*classes: styled-button
	*html
		<i class="fas fa-star"></i>
	*click
		>> starred = 1
```

**CRITICAL: Style text inside components by targeting p elements:**
```guidedtrack
*html
	<style>
		.my-component {
			background: #0885F8 !important;
		}
		.my-component p {
			color: white !important;
		}
	</style>
```

**Show image with HTML:**
```guidedtrack
*html
	<img src="https://example.com/image.jpg" alt="Image">
```

## Common Reusable Patterns

### Banner at Top of Report Page

```guidedtrack
*html
	<style>
		.banner-row {
			display: flex !important;
			align-items: center !important;
			margin: 0 0 20px 0 !important;
			padding: 16px !important;
			background: linear-gradient(135deg, #0885F8 0%, #1e40af 100%) !important;
			border-radius: 12px !important;
			box-shadow: 0 4px 12px rgba(8, 133, 248, 0.2) !important;
		}
		.banner-icon {
			font-size: 32px !important;
			margin-right: 16px !important;
			color: #ffffff !important;
		}
		.banner-title {
			font-weight: 600 !important;
			color: #ffffff !important;
			margin: 0 !important;
		}
    </style>

*html
	<div class="banner-row">
		<i class="fas fa-chart-line banner-icon"></i>
		<h1 class="banner-title">Your Performance</h1>
	</div>
```

### Header Row with Icon

```guidedtrack
*html
	<style>
		.section-header-row {
			display: flex !important;
			align-items: center !important;
		}
		.section-icon {
			font-size: 28px !important;
			margin-right: 12px !important;
			color: #0885F8 !important;
		}
		.section-title {
			font-weight: 600 !important;
			color: #505050 !important;
			margin: 0 !important;
		}
    </style>

*html
	<div class="section-header-row">
		<i class="fas fa-medal section-icon"></i>
		<h2 class="section-title">Overall Rationality Score</h2>
	</div>
```

### Comparison Table

```guidedtrack
*html
	<style>
		.comparison-grid-table {
			width: 100% !important;
			box-shadow: 0 2px 5px rgba(0,0,0,0.1) !important;
			table-layout: fixed !important;
		}
		
		.comparison-grid-table th,
		.comparison-grid-table td {
			border: 1px solid #e0e0e0 !important;
			padding: 10px 5px !important; 
			text-align: center !important;
		}
		
		.comparison-grid-table th {
			background-color: #f8f9fa !important;
			font-weight: bold !important;
		}
		
		 /* Make 1st column wider */
		.comparison-grid-table th:nth-child(1) {
			width: 60% !important;
		}
		.comparison-grid-table th:nth-child(2), 
		.comparison-grid-table th:nth-child(3) {
			width: 20% !important;
		}
		
		.comparison-grid-table tr td:first-child {
			font-size: 15px !important;
		}
		
		/* Make text smaller on mobile */
		@media (max-width: 600px) {
			.comparison-grid-table tr td:first-child {
				font-size: 13px !important;
			}
			.comparison-grid-table {
				font-size: 14px !important;
			}
		}
	</style>

*html
	<table class="comparison-grid-table">
		<thead>
			<tr>
				<th>Scenario</th>
				<th>Your Rating</th>
				<th>Mean Rating</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td>Scenario 1</td>
				<td>5.3</td>
				<td>6.9</td>
			</tr>
			<tr>
				<td>Scenario 2</td>
				<td>9.6</td>
				<td>6.5</td>
			</tr>
			<tr>
				<td>Scenario 3</td>
				<td>4.2</td>
				<td>5.5</td>
			</tr>
		</tbody>
	</table>
```

### Copy to Clipboard Button

```guidedtrack
To share your results with your friends, click the button below to copy a shareable version of your report to your clipboard:

*html
	<style>
		.copy-to-clipboard-button {
			background-color: #2196f3 !important;
			padding: 8px 16px !important;
			margin: 0 !important;
			border: none !important;
		}
		.copy-to-clipboard-button:hover {
			transition: background-color 0.2s ease !important;
			background-color: #1976d2 !important;
		}
		.copy-to-clipboard-message, .copy-to-clipboard-message-active {
			margin-right: 0.5em !important;
		}
		.copy-to-clipboard-button .copy-to-clipboard-message-active,
		.copy-to-clipboard-button.is-active .copy-to-clipboard-message {
			display: none !important;
		}
		.copy-to-clipboard-button.is-active .copy-to-clipboard-message-active {
			display: unset !important;
		}
		.copy-to-clipboard-button .fa.fa-clipboard::before {
			color: white !important;
		}
	</style>
	
	<button class="copy-to-clipboard-button btn">
		<span class="copy-to-clipboard-message">
			Copy your report link
		</span>
		<span class="copy-to-clipboard-message-active">
			Copied!
		</span>
		<i class="fa fa-clipboard"></i>
	</button>

>> payload = {}
>> payload["button"] = ".copy-to-clipboard-button"
>> payload["classes_active"] = ["is-active"]
>> payload["text"] = reportLinkShareable

*trigger: create-copy-to-clipboard-button
	*send: payload
```

### Horizontal Progress Bar

```guidedtrack
-- input: skillScore

*html
	<style>
		.percentile-row {
			display: flex !important;
			justify-content: space-between !important;
			align-items: center !important;
			margin: 0 0 8px 0 !important;
		}
		
		.percentile-label {
			font-weight: 600 !important;
			margin: 0 !important;
			color: #505050 !important;
			font-size: 18px !important;
		}
		
		.percentile-value {
			font-weight: 600 !important;
			color: #0885F8 !important;
			margin: 0 !important;
			font-size: 18px !important;
		}
		
		.progress-bar-container {
			width: 100% !important;
			height: 16px !important;
			background-color: #e5e7eb !important;
			border-radius: 8px !important;
			margin-bottom: 8px !important;
		}
		
		.progress-bar-fill {
			height: 100% !important;
			border-radius: 8px !important;
		}
		
		.progress-fill-green {
			background-color: #22c55e !important;
		}
		
		.score-value-green {
			color: #22c55e !important;
		}
	</style>

*html
	<div class="percentile-row">
		<div class="percentile-label">Your score</div>
		<div class="percentile-value score-value-green">{skillScore}%</div>
	</div>
	<div class="progress-bar-container">
		<div class="progress-bar-fill progress-fill-green" style="width: {skillScore}%;"></div>
	</div>
```

### Row with Icon, Name and Score

```guidedtrack
-- input: skillScore

*html
	<style>
		.skill-row {
			display: flex !important;
			align-items: center !important;
		}
		
		.skill-icon-circle {
			width: 50px !important;
			height: 50px !important;
			border-radius: 50% !important;
			background-color: #22c55e !important;
			display: flex !important;
			align-items: center !important;
			justify-content: center !important;
			margin-right: 16px !important;
		}
		
		.skill-icon {
			font-size: 24px !important;
			color: #ffffff !important;
		}
		
		.skill-title {
			font-size: 20px !important;
			font-weight: 600 !important;
			color: #505050 !important;
			margin: 0 !important;
			flex-grow: 1 !important;
		}
		
		.skill-percentage {
			font-size: 16px !important;
			font-weight: 600 !important;
			color: #ffffff !important;
			background-color: #22c55e !important;
			padding: 6px 12px !important;
			border-radius: 20px !important;
			margin: 0 !important;
		}
	</style>

*html
	<div class="skill-row">
		<div class="skill-icon-circle">
			<i class="fas fa-calculator skill-icon"></i>
		</div>
		<div class="skill-title">Quantitative Reasoning</div>
		<div class="skill-percentage">{skillScore}%</div>
	</div>
```

### Clickable Images

Standard `*images` are not clickable - to make an image clickable, use `*component`:

**Clickable logo that's 20% of screen width:**
```guidedtrack
*html
	<style>
		.nautilus-logo-container {
			width: 20% !important;
			max-width: 400px !important;
			min-width: 200px !important;
			cursor: pointer !important;
			border: 0 !important;
		}
		.nautilus-logo-container img {
			width: 100% !important;
		}
	</style>

*component
	*classes: nautilus-logo-container
	*image: https://images.guidedtrack.com/nautilus_logo_gbqn640.png
	*click
		>> logo_clicked = 1
		*trigger: openUrlInNewTab
			*send: {"url" -> "https://nautil.us/join?source=ClearerThinking"}
```

### Responsive Image Containers

**Center an image and prevent full-width expansion (using responsive sizing):**
```guidedtrack
*html
	<style>
		.logo-container {
			text-align: center !important;
		}
		.logo-container img {
			margin: 0 !important;
		}
		
		/* Make logo a bit smaller on desktop */
		@media (min-width: 768px) {
			.logo-container img {
				width: 80% !important;
				height: auto !important;
			}
		}
	</style>

*html
	<div class="logo-container">
		<img src="https://images.guidedtrack.com/herologos_lvxjgmj.png">
	</div>
```

### Alert/Notification Boxes

```guidedtrack
*html
	<style>
		.red-alert-box {
			background: #fef2f2 !important; 
			border: 0 !important;
			border-left: 4px solid #ef4444 !important;
		}
		.red-alert-box p {
			margin: 0 !important;
		}
	</style>
	
*component 
	*classes: red-alert-box
	Warning!
```

### Toggle Components

```guidedtrack
*label: pageStart

*if: toggle_state = "on"
	*component
		*classes: toggle-active
		ON
		*click
			>> toggle_state = "off"
			*goto: pageStart

*if: toggle_state = "off"
	*component
		*classes: toggle-inactive
		OFF
		*click
			>> toggle_state = "on"
			*goto: pageStart
```

### Links and Text Styling

**Links opening in new tab:**
```guidedtrack
*html
	<a href="https://example.com" target="_blank">Open link in new tab</a>
```

> **Note:** In `*html` components, always use `target="_blank"` to open URLs in new tabs (preferred behavior)

<br>

**Target only a portion of text inside a paragraph:**
```guidedtrack
*html
	<p>Track your quiz progress with the thin <span style="color: #2dbdb4;">blue line</span></p>
```

> **Note:** Use `<span>` to add CSS only to a portion of text inside a paragraph

<br>

## CSS Best Practices & Troubleshooting

### Formatting Best Practices

**Each property on its own line:**
```guidedtrack
*html
	<style>
		.my-class {
			color: #303030 !important;
			font-size: 18px !important;
			margin: 1rem !important;
		}
	</style>
```

**Composability (relevant for clean code):**
```guidedtrack
*html
	<style>
		.my-color {
			color: red !important;
		}

		.my-font-size {
			font-size: 22px !important;
		}
	</style>

*html
	<p class="my-color my-font-size">Hello</p>
```

**Use highly specific selectors to override default CSS properties on Clearer Thinking pages:**
```guidedtrack
*html
	<style>
		.container a.my-button,
		.container a.my-button:link {
			color: white !important;
		}
	</style>
```

### Working with Quotes in HTML

**Adding quotes inside html variables:**
```guidedtrack
>> quote = "%22".decode("url")
>> html_content = "<div class={quote}my-class{quote}>Content</div>"
```

**Single quotes are OK but may cause linter errors:**
```guidedtrack
>> html_content = "<div class='my-class'>Content</div>"
*html
	{html_content}
```

### Tables

**CRITICAL: Must include `<tbody>`:**
```guidedtrack
*html
	<table>
		<tbody>
			<tr>
				<th>Header 1</th>
				<th>Header 2</th>
			</tr>
			<tr>
				<td>Data 1</td>
				<td>Data 2</td>
			</tr>
		</tbody>
	</table>
```

### General Guidelines

- **Units:** Prefer `px` for units in CSS styling over `rem` or `em`
- **Debugging:** "Unsafe markup" linter errors always point to the 1st `*html` block line, not the specific line inside the block causing the issue
- **Sanitization:** GuidedTrack often sanitizes content but usually still renders it correctly. We aim to remove all sanitization/linter errors

### CSS Refactoring Techniques

- Use combined selectors (commas) to reduce repetition
- Create utility classes for commonly used properties
- Group related styles together
- Use desktop-first approach with single mobile media query

```guidedtrack
*html
	<style>
		/* GOOD: Combined selectors */
		.leaderboard-name, .leaderboard-points {
			color: #16a34a !important;
			font-weight: 700 !important;
		}

		/* GOOD: Desktop-first responsive */
		.container { 
			padding: 10px !important; 
		}

		@media (max-width: 640px) {
			.container { 
				padding: 10px !important; 
			}
		}
	</style>
```

### Critical String Handling

**CRITICAL: The `\"` syntax will cause the string to close, use `'` instead:**

**❌ WRONG:**
```guidedtrack
>> options = ["They're the \"engineer\"", "Other option"]
```

**✅ CORRECT:**
```guidedtrack
>> options = ["They're the 'engineer'", "Other option"]
```

### Important Notes

- **Global CSS:** CSS class definitions in an `*html` `<style>` block apply globally on the current page. Redefining a class later affects all elements using it, including those appearing before the redefinition
- **Spacing:** Avoid consecutive comment lines (e.g., two `--` lines in a row) as this can create unwanted vertical space in GuidedTrack outputs

### Border Handling

**Prevent border expansion on Clearer Thinking embedded pages:**
```css
.my-button {
	border: 1px solid #2196f3 !important;
}
```

**Remove default component borders:**
```css
.my-component {
	border: 0 !important;
}
```

### Modern CSS Support

**✅ WORKING:**
- CSS Grid, Flexbox
- Complex selectors like `:nth-child()`, `:hover`, etc.
- Colors: gradients, `rgba()`, `hsla()`, etc. (but we prefer HEX when possible)
- Animations (`@keyframes`) - but SKIP `!important` tags from animation-related CSS properties
- Transitions
- Media queries
- FontAwesome icons

**❌ DO NOT WORK:**
- JavaScript
- SVG elements
- Some advanced filters

## Clearer Thinking Color Palette

### Primary Colors
- **Main blue:** #0885F8
- **Main grey:** #F5F5F5
- **Main dark:** #303030

### Accent Colors
- **Gold:** #FECB02
- **Orange:** #F8911B

### Text Colors
- **Dark:** #303030
- **Middle:** #737373
- **Light:** #A6A6A6

> **Note:** Normal paragraph text, written without any HTML, is by default #505050 in GuidedTrack. You do NOT need to always specify colors, GuidedTrack adds colors by default.

<br>

### Responsive iframe Height

**Toggle the height of iframes:**
```guidedtrack
*html
	<style>
		iframe {height: 440px !important;}
		@media only screen and (max-width: 400px) {
			iframe {height: 270px !important;}
		}
	</style>
```

<br>

# Part 6: Advanced Features

## Email

**Basic email:**
```guidedtrack
*email
	*to: {user_email}
	*subject: Thank you!
	*body
		Great job.
```

**Pass data to programs via URL:**
```guidedtrack
>> reportURL = "https://programs.clearerthinking.org/program-name/report/?score={score}&name={name}"
*email
	*to: {user_email}
	*subject: Survey Results
	*body
		Your score was {score}
		[Click here|{reportURL}] to access your report
```

**Scheduled email:**
```guidedtrack
*email
	*to: {user_email}
	*when: calendar::now + 1.days
	*identifier: reminder_1
	*subject: Don't forget!
```

**Cancel scheduled email:**
```guidedtrack
*email
	*identifier: reminder_1
	*cancel
```

## Time & Calendar

**Current time (format: 'August 3rd, 2025, 10:35 AM'):**
```guidedtrack
>> now = calendar::now
```

**Time arithmetic:**
```guidedtrack
>> in2Hours = calendar::now + 2.hours
>> tomorrow = calendar::now + 1.days
>> nextWeek = calendar::now + 1.weeks
```

**Format time:**
```guidedtrack
>> in_date = calendar::now
*program: date format parser - andre
-- outputs:
-- out_year
-- out_monthText
-- out_monthNumeric
-- out_dayOfMonth
-- out_date
-- out_time
```

## Charts

**Bar chart:**
```guidedtrack
*chart
	*type: bar
	*data: [["Category A", 10], ["Category B", 20]]
```

**Scatter chart:**
```guidedtrack
*chart
	*type: scatter
	*data: [[1989, 100], [1993, 120], [1998, 155]]
```

**Line chart:**
```guidedtrack
*chart
	*type: line
	*data: [[1, 10], [2, 15], [3, 12]]
```

**More custom charts:**
```guidedtrack
*chart
	*type: bar
	*data: [["Label 1", 50]]
		*color: #ff6384
	*data: [["Label 2", 75]]
		*color: #36a2eb
	*yaxis
		*min: 0
		*max: 100
```

## Navigation Menu

**Navigation menu (shown on top/bottom of screen):**
```guidedtrack
*navigation
	Previous
		*icon: glyphicon glyphicon-chevron-left
		*goto: previousPage
	Next page
		*icon: glyphicon glyphicon-chevron-right
		*goto: nextPage
```

**Hide navigation menu (which by default persists across pages):**
```guidedtrack
*navigation: hide
```

**Toggle content with navigation menu:**
```guidedtrack
-- Initialize state variable
>> showRules = "no"

*label: questionPage

*if: showRules = "no"
	*navigation
		Show Rules
			*icon: fa-info-circle
			>> showRules = "yes"
			*goto: questionPage
*if: showRules = "yes"
	*navigation
		Hide Rules
			*icon: fa-times-circle
			>> showRules = "no"
			*goto: questionPage
	
	-- The rules are only displayed when showRules is "yes"
	*header: Language Rules
	*list
		Rule 1: ...
		Rule 2: ...

*question: What is the correct translation?
	*save: answer
```

## Back Button & Points

**Enable back button (go back to previous question):**
```guidedtrack
*settings
	*back: yes
```

**Disable back button:**
```guidedtrack
*settings
	*back: no
```

**Points system (a running total of points is always shown to the user):**
```guidedtrack
*question: What is 2 + 2?
	4
		*points: 2
	5
		*points: -1
```

**Hide the visible points counter:**
```guidedtrack
*points: hide
```

**Show points in text:**
```guidedtrack
Optionally, you can also show points like this: {points}
```

## Page & Login

**Page (show multiple questions without page break):**
```guidedtrack
*page
	*question: First name?
		*save: firstName
	*question: Last name?
		*save: lastName
```

> **Note:** Do NOT add `*button` indented in `*page` (button is added automatically)

<br>

**User login:**
```guidedtrack
*login
	*required: yes
```

> **Note:** If user is logged in with GuidedTrack account, `*login` does nothing. If not, program shows a "Sign in or create an account to continue" button

## API Calls & Services

### Configure Settings

Configure in Settings > Services on GuidedTrack webapp:
- **Name:** Service identifier (e.g., Call OpenAI API)
- **URL:** Base endpoint (e.g., https://api.openai.com/v1)
- **Headers:** Authentication (e.g., Authorization: Bearer [key])

### Make API call in code

**Build payload:**
```guidedtrack
>> payload = {}
>> payload["model"] = "gpt-4o"
>> payload["messages"] = [{"role" -> "user", "content" -> prompt}]
```

**Make request:**
```guidedtrack
*service: Call OpenAI API
	*path: /chat/completions
	*method: POST
	*send: payload
	*success
		>> response = it["choices"][1]["message"]["content"]
	*error
		>> error = it["error"]
```

### OpenRouter API

To access hundreds of AI models through a single API, use the "Call OpenRouter API" subprogram. This requires only 1 API key to access many AI models (from all major providers like OpenAI, Anthropic, Google, xAI, etc.)

**Inputs:**
```guidedtrack
>> prompt_for_openrouter = "What is 2 + 2?"
>> model_for_openrouter = "anthropic/claude-sonnet-4"

*program: Call OpenRouter API
-- output: response_from_openrouter
```

> - Optional parameters: `temperature`, `max_tokens`  
> - Defaults: `temperature=0.7`, `max_tokens=1000`  

### APItemplate for Image Generation

For generating beautiful images (e.g., for sharing results on social media), use APItemplate through their API:

**Generate dynamic poster/image:**
```guidedtrack
>> poster_link = "https://api.apitemplate.io/template_id/image.png?title.text={user_name}&score.text={final_score}&type.text={personality_type}"
```

> **Note:** APItemplate allows you to create beautiful, customized images by passing variables through URL parameters. Each template has its own unique ID.

<br>

# Part 7: Best Practices & Reference

## Coding Principles

- Add comments sparingly, mostly for key stages or non-obvious logic
- **DRY Principle:** Avoid redundant code. Use loops and subprograms for reusable logic (e.g., code used across multiple pages)
- **KISS Principle:** Don't use overcomplicated HTML/CSS where normal built-in functions would look good

## Error Prevention

**Check variable existence before use:**
```guidedtrack
*if: userName
	*if: userName = "John"
		Hello John!
```

**Use single = for comparison (not ==):**
```guidedtrack
*if: value = 10
```

**Arrays must be on single line, or use .add():**

**❌ WRONG:**
```guidedtrack
>> questions = [
	["Q1", "A"],
	["Q2", "B"]
]
```

**✅ CORRECT:**
```guidedtrack
>> questions = []
>> questions.add(["Q1", "A"])
>> questions.add(["Q2", "B"])
```

> **Note:** In general, most GuidedTrack commands must be on a single line, unless within `*html` blocks

## Our Work Ecosystem

**Spark Wave's other main projects, aside from GuidedTrack, include:**
- **Clearer Thinking:** Free tools and programs to improve decision-making
- **Positly:** A platform to recruit study participants from Mechanical Turk, integrates well with GuidedTrack
- **Thought Saver:** A flashcard app
- **Personality Map:** A.I.-generated correlations for millions of personality statements
- **UpLift:** A mental wellness app based on cognitive-behavioral therapy (CBT)
- **Mind Ease:** An app for providing immediate relief from anxiety and panic attacks

<br>

# End of Syntax Guide