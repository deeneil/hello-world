//escape: expand newline and tab into visible sequences
//while copying string t into s
void escape(char* s, char* t)
{
	int i, j;
	i = j = 0;
	for (; t[i] != '\0'; i++)
	{
		switch (t[i])
		{
			case '\t':
				s[j++] = '\\';
				s[j++] = 't';
				break;
			case '\n':
				s[j++] = '\\';
				s[j++] = 'n';
				break;
			default:
				s[j++] = t[i];
				break;
		}
	}
	s[j] = '\0';
}
//unescape: convert escape sequence into real characters
//while copying string t to s
//first type:
void unescape(char* s, char* t)
{
	int i, j;
	for (i = j = 0; t[i] != '\0'; i++)
	{
		if (t[i] != '\\')
		{
			s[j++] = t[i];
		}
		else					//t[i] is a backslash
		{
			switch (t[i])
			{
				case '\n':		//real newline
					putchar('\n');
					break;
				case '\t':		//real tab
					s[j++] = '\t';
					break;
				default:		//all other characters after backslash,just copy them and backslash
					s[j++] = '\\';
					s[j++] = t[i];
					break;
			}
		}
	}
	s[j] = '\0';
}
//second type:switch() can also use nested structure
void unescape(char* s, char* t)
{
	int i, j;
	for (i = j = 0; t[i] != '\0'; i++)
	{
		switch (t[i])
		{
			case '\\':
				switch (t[i])
				{
					case '\n':		//real newline
						putchar('\n');
						break;
					case '\t':		//real tab
						s[j++] = '\t';
						break;
					default:		//all other characters after backslash,just copy them and backslash
						s[j++] = '\\';
						s[j++] = t[i];
						break;
				}
				break;					
			default:
				s[j++] = t[i];
				break;			
		}			
	}
	s[j] = '\0';
}
