# AcademicAI.github.io
AI Website that can help you excel in every subject in school
import { useState } from 'react';
import { useRouter } from 'next/router';
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { motion } from 'framer-motion';
import { ArrowRight } from 'lucide-react';

export default function Home() {
  const router = useRouter();

  const handleNavigation = (subject) => {
    router.push(`/${subject}`);
  };

  return (
    <div className="min-h-screen bg-gray-100 flex flex-col items-center justify-center">
      <motion.h1
        className="text-5xl font-bold mb-8"
        initial={{ opacity: 0, y: -50 }}
        animate={{ opacity: 1, y: 0 }}
      >
        AI Learning Hub
      </motion.h1>
      <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
        {['math', 'science', 'english'].map((subject) => (
          <motion.div
            key={subject}
            whileHover={{ scale: 1.05 }}
            whileTap={{ scale: 0.95 }}
          >
            <Card className="cursor-pointer hover:shadow-lg" onClick={() => handleNavigation(subject)}>
              <CardContent className="p-6 flex flex-col items-center">
                <h2 className="text-2xl font-semibold capitalize">{subject}</h2>
                <Button variant="outline" className="mt-4">
                  Go to {subject} <ArrowRight className="ml-2 w-4 h-4" />
                </Button>
              </CardContent>
            </Card>
          </motion.div>
        ))}
      </div>
    </div>
  );
}
